# Embedding the 90R Bill Tracker dashboard

The dashboard is one self-contained web page. It's rebuilt each evening during the 2027 legislative session (through May 31, 2027) from Texas Legislature Online data and republished at the same address, so an embedded copy always shows the latest version. The host site doesn't need to change anything.

**Dashboard address:** https://darrekf.github.io/tx-legislature-dashboard/

## Embed code

Paste this where the dashboard should appear. The script lets the frame grow and shrink to fit the page, so readers never see a second scroll bar.

```html
<iframe id="tx90r-dashboard" src="https://darrekf.github.io/tx-legislature-dashboard/?theme=light"
        title="90R Bill Tracker: Texas Legislature, 90th Regular Session"
        style="width:100%; height:4300px; border:0;" loading="lazy"></iframe>
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
        style="width:100%; height:4300px; border:0;"></iframe>
```

Since November 26, 2026, the dashboard is one page: a "New this week" box, "Where the bills stand," a **Choose Local Government Types** list and the bill table, which shows 25 bills per page. At desktop widths, 4,300 px fits the whole page. Readers can pick 10, 25, 50 or 100 bills per page, and longer lists and phone screens scroll inside the frame. When the dashboard is embedded, it also shows an **Open the full tracker in a new tab** link at the top, so readers can always reach the whole page.

Approximate heights, with 25 bills per page:

| Frame width | Height |
|---|---|
| 1,100-1,200 px | 4,270-4,290 px |
| 900 px | 4,930 px |
| Phone (about 400 px) | 6,460 px |

## Options

Add these to the end of the address:

- **`?theme=light`** - no longer has any effect. Since November 18, 2026, the page always uses its dark color scheme so the frame stands out from the host page. Existing embeds that include it keep working.
- **`?header=0`** - hides the navy title band, including the logos, when the host page already has its own title.
- **`?view=`** - no longer has any effect. Since November 26, 2026, the dashboard has a single view. Existing embeds that include it keep working.
- **Combined** - join options with `&`, for example `?theme=light&header=0`
- **Links to one type** - add a type name after `#` to open the list on it, for example `#county`, `#school-district` or `#county--city`. Use `#any-local-government` for every bill marked as affecting local government.

## Notes for the web team

- **No outside requests:** the page loads no outside scripts, fonts, cookies or trackers. The data, icons, logos and the code for the table (Tabulator, MIT license) and the search (Fuse.js, Apache 2.0 license) are all built into the file.
- **Links:** each bill number opens its Texas Legislature Online history page in a new tab.
- **Sizing:** the layout adjusts from phone width up to 1,120 px wide.
- **Accessibility:** the local government type list, search box, chamber buttons and sort menu can all be reached by keyboard and have text labels. A review against the university's accessibility standard is still recommended.
- **Branding:** the Bush School mark is the "dark background" version from the 2026 unit identity files, used without changes. The page also carries the City & County Governance Program mark.

## Questions

For questions, comments, or suggestions, [click here](mailto:dferrell@tamu.edu?subject=Feedback%3A%2090R%20Bill%20Tracker).
