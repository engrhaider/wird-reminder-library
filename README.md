# Wird Reminder — library bundle

Static hosting for the Wird Reminder app's content library. **Generated, not
edited by hand.**

The app ships with a copy of this bundle and polls `manifest.json` at most once
a day. When the manifest names a higher version, the app downloads that
`library-vN.db` whole, verifies its checksum, and swaps it in. Nothing here is
an API, and nothing has to stay up for the app to keep working offline.

| File            | What it is                                                         |
| --------------- | ------------------------------------------------------------------ |
| `manifest.json` | Current version, size, and checksums                                |
| `library-vN.db` | The published library as read-only SQLite, with a full-text index   |
| `images/`       | Images for image-type wirds                                         |
| `CNAME`         | Custom domain for GitHub Pages                                      |
| `.nojekyll`     | Stops Jekyll from dropping files whose names begin with an underscore |

It carries curated content only. No user data and no credentials ever reach it.

## Publishing

From the `wird-reminder` repo, never by editing this one:

```bash
php artisan library:export     # build a new bundle
php artisan library:publish    # mirror it here and push
```

`library:publish` deletes bundles the export has pruned, so this repo stays in
step rather than accumulating every version ever built. It never touches
`CNAME`, `.nojekyll`, or this README.
