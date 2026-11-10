# Embedding the 90R Bill Tracker dashboard

The dashboard is one self-contained web page. It's rebuilt each morning during the 2027 legislative session (through May 31, 2027) from Texas Legislature Online data and republished at the same address, so an embedded copy always shows the latest version. The host site doesn't need to change anything.

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

If the content system doesn't allow scripts, the iframe still works by itself. It just uses the fixed height and scrolls inside the frame.

## Options

Add these to the end of the address:

- **`?theme=light`** - always uses the light color scheme. Without it, the page follows each reader's light or dark setting.
- **`?header=0`** - hides the navy title band, including the logos, when the host page already has its own title.
- **Both together** - `?theme=light&header=0`

## Notes for the web team

- **No outside requests:** the page loads no outside scripts, fonts, cookies or trackers. The data, icons and logos are all built into the file.
- **Links:** each bill number opens its Texas Legislature Online history page in a new tab.
- **Sizing:** the layout adjusts from phone width up to 1,120 px wide.
- **Accessibility:** the charts can be reached by keyboard and have text labels. Every number in them can also be found in the searchable bill table. A review against the university's accessibility standard is still recommended before launch.
- **Branding:** the Bush School mark is the "dark background" version from the 2026 unit identity files, used without changes. The page also carries the City & County Governance Program mark.
