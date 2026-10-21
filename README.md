# EFNAST – Edge-Fainted Noisy Scene Text dataset (train / test split)

```
train/images   951 images      train/gt   951 annotation files
test/images    321 images      test/gt    321 annotation files
```

Every image `train/images/<name>.<ext>` has its annotation in `train/gt/` with the same subset prefix
(the same applies to `test/`):


`###` marks illegible (do-not-care) text; `difficult = 1` marks difficult text lines in NAST2.
Annotation files are unchanged from the originals (UTF-8, some with a BOM); only file names were prefixed.

The split was made with a fixed random seed (2026), stratified by subset, at the 951:321 train/test ratio.
No image appears in both train and test.
