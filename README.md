# notion-widgets

This is a collection of code used by Prof C in his Notion database. 

What time is it here when it is ____ in ____\
https://jscottmo.github.io/notion-widgets/chronometer.html?view=from

What time is it in ___ when it is ___ here\
https://jscottmo.github.io/notion-widgets/chronometer.html?view=to

Time in places where collaborators are\
https://jscottmo.github.io/notion-widgets/chronometer.html?view=clock

Holidays in places where collaborators are\
https://jscottmo.github.io/notion-widgets/daysoff.html

Create a calendar file to time block a month's work at a time (in development)\
https://jscottmo.github.io/notion-widgets/publishingcadence.html

## Image Carousel (`carousel.html`)

A simple image carousel you can embed on any Notion page, including public ones. Viewers move between images with the arrows, the dots, a swipe on a phone, or the left/right arrow keys. It doesn't advance on its own.

The images are stored in a separate GitHub repo, [`carousel-images`](https://github.com/JScottMO/carousel-images), so they never expire. This one `carousel.html` file can run any number of carousels.

### Quick start

1. **Name your images** with a short prefix and a number, starting at 1, with no gaps:
   `talks1.png`, `talks2.png`, `talks3.png` …
2. **Upload them** to the `carousel-images` repo: **Add file → Upload files**, drag the files in, then click **Commit changes**.
3. **Embed in Notion.** Type `/embed` and paste:

   ```
   https://jscottmo.github.io/notion-widgets/carousel.html?set=talks&repo=carousel-images
   ```

4. **Resize** the embed by dragging the bottom edge of the block in Notion.

### URL options

| Option | What it does | Example |
|---|---|---|
| `set=` | **Required.** The filename prefix. `set=talks` shows `talks1`, `talks2`, … | `set=talks` |
| `repo=` | The GitHub repo holding the images | `repo=carousel-images` |
| `ext=` | File type. The default is `png`. | `ext=jpg`, `ext=gif` |
| `fit=cover` | Fills the frame and crops the edges. The default shows the whole image. | `fit=cover` |
| `bg=` | Background color as a hex code, without the `#` | `bg=ffffff` |
| `v=` | Cache-buster. Change the number after replacing images. | `v=2` |

Add options with `&`:

```
https://jscottmo.github.io/notion-widgets/carousel.html?set=talks&repo=carousel-images&ext=jpg&v=2
```

### Multiple carousels

Give each carousel its own prefix. They can all live in the same image repo:

| Files in `carousel-images` | Embed URL uses |
|---|---|
| `talks1.png` … `talks6.png` | `set=talks` |
| `events1.png` … `events4.png` | `set=events` |
| `book1.png` … `book3.png` | `set=book` |

### Rules to remember

- **Numbers start at 1 and can't skip.** The carousel stops at the first missing number, so if `talks3.png` is missing, `talks4.png` won't show.
- **Names are case-sensitive.** `Talks1.png` or `talks1.PNG` won't match `set=talks`. Keep everything lowercase.
- **One file type per carousel.** Don't mix `.png` and `.gif` in the same set.
- **Animated GIFs work.** Add `&ext=gif`. Keep each file under a few MB, because GitHub's website rejects files over 25 MB.
- **Changes take a minute or two** to show up after you commit. If Notion still shows old images, change `v=` in the embed URL (for example, `v=2` to `v=3`).

### Updating a carousel

- **Replace an image:** upload a new file with the exact same name. GitHub overwrites the old one. Then bump `v=`.
- **Add an image:** upload the next number in the sequence, such as `talks7.png`.
- **Remove an image:** delete it and renumber the files after it so there are no gaps.

### Troubleshooting

| Message or problem | Likely cause |
|---|---|
| "No images found. Expected …/talks1.png" | The first file is missing or misnamed. Check the prefix, the number, the capitalization, and `ext=`. |
| Only some images show | There's a gap in the numbering, or one file has a different extension. |
| Old images still showing | Browser or Notion cache. Change the `v=` number. |
| 404 on the carousel itself | Use the `jscottmo.github.io/...` address, not `github.com/...`. |
