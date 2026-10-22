#Blackscreen

A minimal web page that **simulates a switched-off smartphone screen**.

Born from a real problem: listening to YouTube with the phone in your pocket, **without a Premium subscription**. No background playback, and every accidental touch in your pocket starts random videos, pauses, or switches tabs. Blackscreen solves it with three simple ideas:

- **Screen on, but black** — the Wake Lock API keeps the screen awake (so playback never stops), while a full-screen black overlay makes it look off. On OLED displays, true black draws very little power.
- **Touches ignored** — every accidental tap, swipe, pinch or scroll is intercepted and discarded.
- **Gesture-based unlock** — leaving the overlay requires an intentional sequence that can never be triggered by accident in a pocket.

##How to use

1. Start a video on YouTube in another browser tab (with your ad blocker, if you like).
2. Open Blackscreen and press **⬛ Activate**.
3. Put the phone in your pocket: audio keeps playing, the screen stays black, touches do nothing.

On Vivaldi (and Chromium-based browsers on Android in general), playback continues even when the YouTube tab is not visible — that's the workflow this page is designed for.

##Gestures

| Gesture | Action |
| --- | --- |
| Press and hold one finger ~1.5 s, then swipe (~80 px in any direction) | Unlocks the screen |
| Any other tap, swipe, pinch or scroll | No effect |

For pausing, use the system media controls or your headphones' buttons: a web page cannot control a different tab.

## Hosting

The page is a **single HTML file**, with no dependencies, frameworks or build step. Any static hosting will do.

### GitHub Pages

1. Create a repository and upload the page renamed as `index.html`.
2. In the repository: **Settings → Pages**.
3. Source: *Deploy from a branch* → branch `main`, folder `/ (root)` → **Save**.
4. After a few minutes the page is live at `https://<yourusername>.github.io/<repo>/`.

Tip: use "Add to Home screen" in your browser to open it with a single tap.

##Known limitations

- The Blackscreen tab must stay **in the foreground**: switching to another app or locking the phone stops playback.
- The **Wake Lock** requires a Chromium-based browser or Safari 16.4+; with battery saver enabled the browser may refuse it (the page shows a discreet warning).
- Edge swipes (back gesture, notification shade) are handled by the operating system and cannot be blocked by a web page.
- If your browser pauses background tabs, YouTube audio will stop: Blackscreen cannot prevent this.

## 🔧 Technical details

- **One single file**, zero dependencies, zero external APIs: it even works offline once loaded.
- `Screen Wake Lock API` with automatic re-acquisition when returning to the foreground (`visibilitychange`).
- Full-screen overlay with `touch-action: none` and preventive interception of all touch/mouse events, plus blocking of context menus, selection and dragging.
- Automatic fullscreen when supported, to reduce system edge gestures.
- Gesture engine based on press duration + swipe distance, designed so that random pocket contact never triggers anything.

## 📄 License

To be defined — if you publish the repository, add your license of choice here (e.g. MIT).

## ™️ Trademark notice

Blackscreen is an independent project and is not affiliated with, sponsored by, or endorsed by YouTube or Google. YouTube is a trademark of Google LLC.
