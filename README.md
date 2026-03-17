# Tiny Wins Stickers

A static sticker catalog and image host for the Tiny Wins mobile app. Deployed to Vercel as a purely static site—no server code, API, or database.

## Catalog URL

Once deployed, the catalog is available at:

```
https://tinywinssticker.vercel.app/catalog.json
```

## Project Structure

```
tinywins-stickers/
  public/
    catalog.json          # Sticker pack catalog (consumed by the app)
    stickers/
      {pack_id}/          # One folder per pack
        *.png             # Sticker images
  vercel.json
  README.md
```

## Adding New Packs

1. **Add PNG files** to `public/stickers/{pack_id}/`
   - Use square images with transparent backgrounds
   - Name files consistently (e.g. `{pack_id}_01.png`, `{pack_id}_02.png`)

2. **Update `catalog.json`** with the new pack entry:
   ```json
   {
     "id": "pack_id",
     "name": "Pack Name",
     "stickerCount": 3,
     "sizeBytes": 123456,
     "baseUrl": "https://tinywinssticker.vercel.app/stickers/pack_id",
     "stickers": [
       { "id": "pack_id_01", "name": "Sticker 01", "filename": "pack_id_01.png" }
     ]
   }
   ```
   - Set `sizeBytes` to the total size (in bytes) of all PNG files in the pack
   - Ensure `baseUrl` has no trailing slash

3. **Push and deploy** — Vercel will automatically deploy on push

## Deployment

1. Connect this repo to Vercel
2. In **Project Settings → General → Root Directory**, set to `public`
3. Deploy — the site serves static files only (no build step)
