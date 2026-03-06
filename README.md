# crop-image-skill

Skill repository for the deployed Crop Image API.

- Website: https://imageclaw.net
- Docs: https://api.imageclaw.net/docs
- API Base URL: https://api.imageclaw.net
- Status/Health URL: https://api.imageclaw.net/health

## Structure

```text
crop-image-skill/
├── README.md
├── SKILL.md
└── skills/
    └── crop-image/
        └── SKILL.md
```

## Install / Verify

```bash
npx skills add <owner>/<repo> --list
```

## API Example (Success)

Request:

```bash
curl -sS -X POST "https://api.imageclaw.net/crop" \
  -H "content-type: application/json" \
  -d '{
    "url": "https://picsum.photos/800/600",
    "width": 200,
    "height": 200
  }'
```

Response:

```json
{
  "cropped_url": "https://crop.imagebee.net/crops/1772761350_b8050bd6ec26.jpg",
  "original_size": [800, 600],
  "face_detected": false
}
```

## API Example (Failure)

Request with invalid image URL:

```bash
curl -sS -X POST "https://api.imageclaw.net/crop" \
  -H "content-type: application/json" \
  -d '{
    "url": "https://example.com/not-an-image",
    "width": 200,
    "height": 200
  }'
```

Response (`400`):

```json
{
  "detail": "URL does not point to a valid image"
}
```
