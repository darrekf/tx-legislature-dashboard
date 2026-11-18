# Embedding the 90R Bill Tracker dashboard

The dashboard is one self-contained web page. It's rebuilt each evening during the 2027 legislative session (through May 31, 2027) from Texas Legislature Online data and republished at the same address, so an embedded copy always shows the latest version. The host site doesn't need to change anything.

**Dashboard address:** https://darrekf.github.io/tx-legislature-dashboard/

## Embed code

Paste this where the dashboard should appear. The script lets the frame grow and shrink to fit the page, so readers never see a second scroll bar.

```html
<iframe id="tx90r-dashboard" src="https://darrekf.github.io/tx-legislature-dashboard/?theme=light"
        title="90R Bill Tracker: Texas Legislature, 90th Regular Session"
        style="width:100%; height:3200px; border:0;" loading="lazy"></iframe>
<script>
  window.addEventListener('message', function (e) {
    if (e.origin === 'https://darrekf.github.io' && e.data && e.data.type === 'tx90r-dashboard-height') {
      document.getElementById('tx90r-dashboard').style.height = e.data.height + 'px';
    }
  });
</script>
```

**The script is what makes the frame fit.** Without it, the frame stays at the height set in the iframe tag, and anything below that is cut off or has to be scrolled inside the frame. Some content systems remove `<script>` tags from pasted HTML. If yours does, ask whether a "full HTML" format or the page's custom code area can keep it, or use the no-script setup below.

## If scripts aren't allowed

Use the iframe alone, with a fixed height, and make sure the frame can scroll. Don't add `scrolling="no"` or `overflow: hidden` to it.

```html
<iframe src="https://darrekf.github.io/tx-legislature-dashboard/?theme=light"
        title="90R Bill Tracker: Texas Legislature, 90th Regular Session"
        style="width:100%; height:3700px; border:0;"></iframe>
```

The dashboard opens with **All** sections showing. At desktop widths, 3,700 px fits the whole dashboard with 10 bills listed. Readers can use the **Select What to Show** buttons (All, Overview, Session, Find a bill) to see one part at a time. Longer bill lists and phone screens scroll inside the frame. When the dashboard is embedded, it also shows an **Open the full tracker in a new tab** link next to those buttons, so readers can always reach the whole page.

For a shorter frame, open on a single section by adding `&view=overview` to the address and setting the height to 2,700 px. That fits any single section at desktop widths.

Approximate heights, with 10 bills listed:

| Frame width | All | Overview | Session | Find a bill |
|---|---|---|---|---|
| 1,100-1,300 px | 3,570-3,640 px | 1,470 px | 1,140 px | 2,520-2,590 px |
| 900 px | 4,440 px | 1,590 px | 1,220 px | 3,360 px |
| Phone (about 400 px) | 6,820 px | 2,770 px | 1,990 px | 4,770 px |

## Options

Add these to the end of the address:

- **`?theme=light`** - no longer has any effect. Since November 18, 2026, the page always uses its dark color scheme so the frame stands out from the host page. Existing embeds that include it keep working.
- **`?header=0`** - hides the navy title band, including the logos, when the host page already has its own title.
- **`?view=overview`**, **`?view=session`** or **`?view=find`** - opens on that section instead of All, the default.
- **Combined** - join options with `&`, for example `?theme=light&header=0&view=find`

## Notes for the web team

- **No outside requests:** the page loads no outside scripts, fonts, cookies or trackers. The data, icons and logos are all built into the file.
- **Links:** each bill number opens its Texas Legislature Online history page in a new tab.
- **Sizing:** the layout adjusts from phone width up to 1,120 px wide.
- **Accessibility:** the charts can be reached by keyboard and have text labels. Every number in them can also be found in the searchable bill table. A review against the university's accessibility standard is still recommended before launch.
- **Branding:** the Bush School mark is the "dark background" version from the 2026 unit identity files, used without changes. The page also carries the City & County Governance Program mark.

## Questions

For questions, comments, or suggestions, [click here](mailto:dferrell@tamu.edu?subject=Feedback%3A%2090R%20Bill%20Tracker).
