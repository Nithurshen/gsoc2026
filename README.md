# GSoC 2026: Multi-threaded Extraction for `fsck.erofs`

Final report for my Google Summer of Code 2026 project with the
[EROFS](https://erofs.docs.kernel.org/) filesystem.

**Report: https://nithurshen.github.io/gsoc2026/**

The work is two patches to erofs-utils, applied by the maintainer to the
[`experimental-mt-extraction`](https://git.kernel.org/pub/scm/linux/kernel/git/xiang/erofs-utils.git/log/?h=experimental-mt-extraction)
branch on 19 October 2026:

| Patch | Commit | Mailing list |
|---|---|---|
| [PATCH 1/2] fsck.erofs: implement concurrent directory traversal | [`a54dbf5`](https://git.kernel.org/pub/scm/linux/kernel/git/xiang/erofs-utils.git/commit/?h=experimental-mt-extraction&id=a54dbf580b6fe19309b33764696822b8d5245214) | [lore](https://lore.kernel.org/linux-erofs/20260919151443.29012-2-nithurshen.dev@gmail.com/) |
| [PATCH 2/2] fsck.erofs: add multi-threaded decompression | [`35330f7`](https://git.kernel.org/pub/scm/linux/kernel/git/xiang/erofs-utils.git/commit/?h=experimental-mt-extraction&id=35330f7706fb85df141dc52462b4c5339a266d86) | [lore](https://lore.kernel.org/linux-erofs/20260919151443.29012-3-nithurshen.dev@gmail.com/) |

Together they cut extraction time by 25–35% for lz4hc and zstd and by
72–77% for LZMA (best of 10 runs, against current `master`).

## Structure

- `index.html`: the report page (plain HTML and JS, no build step)
- `style.css`: styles (light/dark, responsive)
- `patches/`: the two patches and the whole series as one mbox

## Applying the patches

```sh
git clone https://git.kernel.org/pub/scm/linux/kernel/git/xiang/erofs-utils.git
cd erofs-utils
git checkout -b mt-extraction v1.9.4
git am /path/to/patches/fsck-erofs-mt-extraction.mbox
```

## Local preview

Open `index.html` in a browser, or run `python3 -m http.server` and visit http://localhost:8000.

## License

The site's code (HTML, CSS and JS) is licensed under Apache-2.0; see [LICENSE](LICENSE).
The patches in `patches/` modify erofs-utils and keep its licences, as given in the
SPDX header of each file they touch.
The written content and benchmark results are © K S Nithurshen; all rights reserved.
