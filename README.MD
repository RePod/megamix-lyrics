Collection of pre-converted lyric files and the rare manual translation copy/paste or retiming.
Have fun cloning a bunch of small files!

Unfortunately there are too many for GH to list so the repo will need to be downloaded/cloned to get something specific out.

There is no consensus (from mod creators) of *what* form of Japanese should be in `_jp` or `_en` so there's a mix of glyphs, romaji, and actual English translations!

- [Song ID List](https://docs.google.com/spreadsheets/d/19ZDbcFfMZHHQWNZD2voBrbKJFRxshdSSt9xknNxSVLM/edit)
- [LyricsPatch](https://gamebanana.com/mods/414986)
- [Generator](https://github.com/Jay184/megamixplus-lyrics-generator)

```Batch
mklink /J "LyricsPatch\lyrics" "path\to\repo\lyrics"
```

# Generating

- Search *.dsc in mods folder
- Copying all of them into the converter's rom/script/ folder
- Combine all mod_pv_db.txt (with the lyrics you want to extract) into a single one or do the NEXT step per mod
- Combined mod_/pv_db from mods folder:
  - Diva JSON Generator's `combined_mod_pv_db.txt` for selected packs
  - Your favorite shell: `cat ./*/*/mod_pv_db.txt > mod_pv_db.txt`
  - Your favorite cmd: `for /R %f in (mod_pv_db.txt) do type "%f" >> combined_mod_pv_db.txt` (don't want to include itself)
- From the generator folder: 
  - `python -m venv venv && venv\Scripts\activate.bat` (required)
  - `pip install -r requirements.txt` (first time)
  - `python lyrics-generator convert-all --db mod_pv_db.txt --destination generated .`
  - If you're feeling daring you can direct `--db` and `--destination` to the places right in the mod folder, but you can't do that in bulk
- Move generated .tomls in `generated/` to `mods/LyricsPatch/lyrics/`
