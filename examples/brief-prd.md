# Brief PRD Example

## Product

Mood Garden is a lightweight mobile app feature for casual emotional journaling. Users should be able to record a small positive moment without feeling pressured to keep a streak.

## Goal

Help users quickly save a small moment and see it grow into a flower over time.

## Core Flow

1. User enters the home screen.
2. User taps "Plant a Flower".
3. User writes a short text note.
4. User can optionally add up to 9 images.
5. User can optionally add 1 main sticker.
6. User submits the note.
7. App shows a growth result.
8. User can open the garden and view the flower detail.

## Rules

- Text limit: 300 characters.
- Supported formats: text, images, text + images, sticker.
- MVP does not support rich formatting or free sticker dragging.
- Three records grow one flower:
  - first record: seed
  - second record: sprout
  - third record: bloom
- Flower type priority:
  - sticker
  - mixed text and images
  - image
  - long text
  - plain text

## States And Exceptions

- Empty content: ask the user to add a little content.
- Privacy-like content: remind the user to use safer wording.
- High-risk content: save quietly without normal celebration.
- Submit failure: keep the content and allow retry.
- Network failure: cache locally and retry later.

## Review Needs

The prototype should be mobile-shaped, low fidelity, and useful for product/design/engineering/QA review.
