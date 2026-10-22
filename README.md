# EFNAST – Edge-Fainted Noisy Scene Text dataset (train / test split)

```
train/images   951 images      train/gt   951 annotation files
test/images    321 images      test/gt    321 annotation files
```

Every image `train/images/<name>.<ext>` has its annotation in `train/gt/` with the same subset prefix
(the same applies to `test/`):

| Prefix | Train | Test | Annotation format (one text instance per line) |
|---|---|---|---|
| `NAST1_` | 76 | 25 | `x1 y1 x2 y2 "text"` – axis-aligned word box (`NAST1_100.jpg` → `NAST1_gt_100.txt`) |
| `NAST2_` | 224 | 76 | `index difficult x y w h angle` – rotated text-line box, angle in radians (`NAST2_IMG_0059.JPG` → `NAST2_IMG_0059.gt`) |
| `NAST3_` | 262 | 88 | `x1,y1,...,x4,y4,script,text` – 4-point word box (`NAST3_img_1.jpg` → `NAST3_gt_img_1.txt`) |
| `Fog_` | 188 | 63 | `x1,y1,...,x4,y4,text` – 4-point word box (`Fog_img_750.jpg` → `Fog_img_750.txt`) |
| `Rain_` | 187 | 63 | `x1,y1,...,x4,y4,text` – 4-point word box (`Rain_img_1.jpg` → `Rain_img_1.txt`) |
| `Other_` | 10 | 3 | `x1,y1,...,x4,y4,text` – 4-point word box (`Other_img_01.jpg` → `Other_gt_img_01.txt`) |
| `Extra_` | 4 | 3 | `x1,y1,...,x4,y4,text` – 4-point word box (`Extra_1206.jpg` → `Extra_gt_1206.txt`) |
| **Total** | **951** | **321** | |

`###` marks illegible (do-not-care) text; `difficult = 1` marks difficult text lines in NAST2.
Annotation files are unchanged from the originals (UTF-8, some with a BOM); only file names were prefixed.
The one exception is the `Other_` subset: the boxes supplied for 11 of its 13 images did not line up with
the text in the image, so those 11 files were re-annotated (word-level boxes, same transcriptions);
`Other_gt_img_01.txt` and `Other_gt_img_03.txt` are unchanged. The `Extra_` subset (7 images) was annotated
for this release in the same word-level format.

The split was made with a fixed random seed, stratified by subset, at the 951:321 train/test ratio
(the `Other_` and `Extra_` subsets were added later without moving any earlier image).
No image appears in both train and test.
