---
tags:
  - "data"
context:
  - "[[WebGL2]]"
---

# WebGL2 Texture Formats

Supported [[Texture]] formats in [[WebGL2]].

---

**Legend**:

- A single number like `8` means 8bits that will be normalized from `0` to `1`.
- A number preceded by an `s` like `s8` means a signed 8bit number that will be normalized from `-1` to `1`.
- A number preceded by an `f` like `f16` means a floating point number.
- A number preceded by a `i` like `i8` means an integer number.
- A number preceded by a `ui` like `ui8` means an unsigned integer number.
- Highlights with # mean they are available in WebGL2 but they are not marked as either color renderable and/or texture filterable by default. Both of those features are available as optional extensions in WebGL2.

## Un-sized Formats

| Format          | Type                   | Channels | Bytes per pixel |
| --------------- | ---------------------- | -------- | --------------- |
| RGBA            | UNSIGNED_BYTE          | 4        | 4               |
| RGB             | UNSIGNED_BYTE          | 3        | 3               |
| RGBA            | UNSIGNED_SHORT_4_4_4_4 | 4        | 2               |
| RGBA            | UNSIGNED_SHORT_5_5_5_1 | 4        | 2               |
| RGB             | UNSIGNED_SHORT_5_6_5   | 3        | 2               |
| LUMINANCE_ALPHA | UNSIGNED_BYTE          | 2        | 2               |
| LUMINANCE       | UNSIGNED_BYTE          | 1        | 1               |
| ALPHA           | UNSIGNED_BYTE          | 1        | 1               |

## Sized Formats

| Sized Format   | Base Format | R bits | G bits | B bits | A bits | Shared bits | Color renderable | Texture filterable |
| -------------- | ----------- | ------ | ------ | ------ | ------ | ----------- | ---------------- | ------------------ |
| R8             | RED         | 8      |        |        |        |             | true             | true               |
| R8_SNORM       | RED         | s8     |        |        |        |             |                  | true               |
| RG8            | RG          | 8      | 8      |        |        |             | true             | true               |
| RG8_SNORM      | RG          | s8     | s8     |        |        |             | true             | true               |
| RGB8           | RGB         | 8      | 8      | 8      |        |             | true             | true               |
| RGB8_SNORM     | RGB         | s8     | s8     | s8     |        |             | true             | true               |
| RGB565         | RGB         | 5      | 6      | 5      |        |             | true             | true               |
| RGBA4          | RGBA        | 4      | 4      | 4      | 4      |             | true             | true               |
| RGB5_A1        | RGBA        | 5      | 5      | 5      | 1      |             | true             | true               |
| RGBA8          | RGBA        | 8      | 8      | 8      | 8      |             | true             | true               |
| RGBA8_SNORM    | RGBA        | s8     | s8     | s8     | s8     |             |                  | true               |
| RGB10_A2       | RGBA        | 10     | 10     | 10     | 2      |             | true             | true               |
| RGB10_A2UI     | RGBA        | ui10   | ui10   | ui10   | ui2    |             | true             |                    |
| SRGB8          | RGB         | 8      | 8      | 8      |        |             | true             | true               |
| SRGB8_ALPHA8   | RGBA        | 8      | 8      | 8      | 8      |             | true             | true               |
| R16F           | RED         | f16    |        |        |        |             | #                | true               |
| RG16F          | RG          | f16    | f16    |        |        |             | #                | true               |
| RGB16F         | RGB         | f16    | f16    | f16    |        |             | #                | true               |
| RGBA16F        | RGBA        | f16    | f16    | f16    | f16    |             | #                | true               |
| R32F           | RED         | f32    |        |        |        |             | #                | #                  |
| RG32F          | RG          | f32    | f32    |        |        |             | #                | #                  |
| RGB32F         | RGB         | f32    | f32    | f32    |        |             | #                | #                  |
| RGBA32F        | RGBA        | f32    | f32    | f32    | f32    |             |                  | #                  |
| R11F_G11F_B10F | RGB         | f11    | f11    | f10    |        |             |                  | true               |
| RGB9_E5        | RGB         | 9      | 9      | 9      |        | 5           |                  | true               |
| R8I            | RED         | i8     |        |        |        |             | true             |                    |
| R8UI           | RED         | ui8    |        |        |        |             | true             |                    |
| R16I           | RED         | i16    |        |        |        |             | true             |                    |
| R16UI          | RED         | ui16   |        |        |        |             | true             |                    |
| R32I           | RED         | i32    |        |        |        |             | true             |                    |
| R32UI          | RED         | ui32   |        |        |        |             | true             |                    |
| RG8I           | RG          | i8     | i8     |        |        |             | true             |                    |
| RG8UI          | RG          | ui8    | ui8    |        |        |             | true             |                    |
| RG16I          | RG          | i16    | i16    |        |        |             | true             |                    |
| RG16UI         | RG          | ui16   | ui16   |        |        |             | true             |                    |
| RG32I          | RG          | i32    | i32    |        |        |             | true             |                    |
| RG32UI         | RG          | ui32   | ui32   |        |        |             | true             |                    |
| RGB8I          | RGB         | i8     | i8     | i8     |        |             |                  |                    |
| RGB8UI         | RGB         | ui8    | ui8    | ui8    |        |             |                  |                    |
| RGB16I         | RGB         | i16    | i16    | i16    |        |             |                  |                    |
| RGB16UI        | RGB         | ui16   | ui16   | ui16   |        |             |                  |                    |
| RGB32I         | RGB         | i32    | i32    | i32    |        |             |                  |                    |
| RGB32UI        | RGB         | ui32   | ui32   | ui32   |        |             |                  |                    |
| RGBA8I         | RGBA        | i8     | i8     | i8     | i8     |             | true             |                    |
| RGBA8UI        | RGBA        | ui8    | ui8    | ui8    | ui8    |             | true             |                    |
| RGBA16I        | RGBA        | i16    | i16    | i16    | i16    |             | true             |                    |
| RGBA16UI       | RGBA        | ui16   | ui16   | ui16   | ui16   |             | true             |                    |
| RGBA32I        | RGBA        | i32    | i32    | i32    | i32    |             | true             |                    |
| RGBA32UI       | RGBA        | ui32   | ui32   | ui32   | ui32   |             | true             |                    |

## Depth and Stencil Formats

| SizedFormat        | BaseFormat      | Depth bits | Stencil bits |
| ------------------ | --------------- | ---------- | ------------ |
| DEPTH_COMPONENT16  | DEPTH_COMPONENT | 16         |              |
| DEPTH_COMPONENT24  | DEPTH_COMPONENT | 24         |              |
| DEPTH_COMPONENT32F | DEPTH_COMPONENT | f32        |              |
| DEPTH24_STENCIL8   | DEPTH_STENCIL   | 24         | ui8          |
| DEPTH32F_STENCIL8  | DEPTH_STENCIL   | f32        | ui8          |

## Compatibility

| Internal Format                         | Format          | Type                           | Source Bytes Per Pixel |
| --------------------------------------- | --------------- | ------------------------------ | ---------------------- |
| RGBA8, RGB5_A1, RGBA4, SRGB8_ALPHA8     | RGBA            | UNSIGNED_BYTE                  | 4                      |
| RGBA8_SNORM                             | RGBA            | BYTE                           | 4                      |
| RGBA4                                   | RGBA            | UNSIGNED_SHORT_4_4_4_4         | 2                      |
| RGB5_A1                                 | RGBA            | UNSIGNED_SHORT_5_5_5_1         | 2                      |
| RGB10_A2, RGB5_A1                       | RGBA            | UNSIGNED_INT_2_10_10_10_REV    | 4                      |
| RGBA16F                                 | RGBA            | HALF_FLOAT                     | 8                      |
| RGBA32F, RGBA16F                        | RGBA            | FLOAT                          | 16                     |
| RGBA8UI                                 | RGBA_INTEGER    | UNSIGNED_BYTE                  | 4                      |
| RGBA8I                                  | RGBA_INTEGER    | BYTE                           | 4                      |
| RGBA16UI                                | RGBA_INTEGER    | UNSIGNED_SHORT                 | 8                      |
| RGBA16I                                 | RGBA_INTEGER    | SHORT                          | 8                      |
| RGBA32UI                                | RGBA_INTEGER    | UNSIGNED_INT                   | 16                     |
| RGBA32I                                 | RGBA_INTEGER    | INT                            | 16                     |
| RGB10_A2UI                              | RGBA_INTEGER    | UNSIGNED_INT_2_10_10_10_REV    | 4                      |
| RGB8, RGB565, SRGB8                     | RGB             | UNSIGNED_BYTE                  | 3                      |
| RGB8_SNORM                              | RGB             | BYTE                           | 3                      |
| RGB565                                  | RGB             | UNSIGNED_SHORT_5_6_5           | 2                      |
| R11F_G11F_B10F                          | RGB             | UNSIGNED_INT_10F_11F_11F_REV   | 4                      |
| RGB9_E5                                 | RGB             | UNSIGNED_INT_5_9_9_9_REV       | 4                      |
| RGB16F, R11F_G11F_B10F, RGB9_E5         | RGB             | HALF_FLOAT                     | 6                      |
| RGB32F, RGB16F, R11F_G11F_B10F, RGB9_E5 | RGB             | FLOAT                          | 12                     |
| RGB8UI                                  | RGB_INTEGER     | UNSIGNED_BYTE                  | 3                      |
| RGB8I                                   | RGB_INTEGER     | BYTE                           | 3                      |
| RGB16UI                                 | RGB_INTEGER     | UNSIGNED_SHORT                 | 6                      |
| RGB16I                                  | RGB_INTEGER     | SHORT                          | 6                      |
| RGB32UI                                 | RGB_INTEGER     | UNSIGNED_INT                   | 12                     |
| RGB32I                                  | RGB_INTEGER     | INT                            | 12                     |
| RG8                                     | RG              | UNSIGNED_BYTE                  | 2                      |
| RG8_SNORM                               | RG              | BYTE                           | 2                      |
| RG16F                                   | RG              | HALF_FLOAT                     | 4                      |
| RG32F, R16F                             | RG              | FLOAT                          | 8                      |
| RG8UI                                   | RG_INTEGER      | UNSIGNED_BYTE                  | 2                      |
| RG8I                                    | RG_INTEGER      | BYTE                           | 2                      |
| RG16UI                                  | RG_INTEGER      | UNSIGNED_SHORT                 | 4                      |
| RG16I                                   | RG_INTEGER      | SHORT                          | 4                      |
| RG32UI                                  | RG_INTEGER      | UNSIGNED_INT                   | 8                      |
| RG32I                                   | RG_INTEGER      | INT                            | 8                      |
| R8                                      | RED             | UNSIGNED_BYTE                  | 1                      |
| R8_SNORM                                | RED             | BYTE                           | 1                      |
| R16F                                    | RED             | HALF_FLOAT                     | 2                      |
| R32F                                    | RED             | FLOAT                          | 4                      |
| R8UI                                    | RED_INTEGER     | UNSIGNED_BYTE                  | 1                      |
| R8I                                     | RED_INTEGER     | BYTE                           | 1                      |
| R16UI                                   | RED_INTEGER     | UNSIGNED_SHORT                 | 2                      |
| R16I                                    | RED_INTEGER     | SHORT                          | 2                      |
| R32UI                                   | RED_INTEGER     | UNSIGNED_INT                   | 4                      |
| R32I                                    | RED_INTEGER     | INT                            | 4                      |
| DEPTH_COMPONENT16                       | DEPTH_COMPONENT | UNSIGNED_SHORT                 | 2                      |
| DEPTH_COMPONENT24, DEPTH_COMPONENT16    | DEPTH_COMPONENT | UNSIGNED_INT                   | 4                      |
| DEPTH_COMPONENT32F                      | DEPTH_COMPONENT | FLOAT                          | 4                      |
| DEPTH24_STENCIL8                        | DEPTH_STENCIL   | UNSIGNED_INT_24_8              | 4                      |
| DEPTH32F_STENCIL8                       | DEPTH_STENCIL   | FLOAT_32_UNSIGNED_INT_24_8_REV | 8                      |
| RGBA                                    | RGBA            | UNSIGNED_BYTE                  | 4                      |
| RGBA                                    | RGBA            | UNSIGNED_SHORT_4_4_4_4         | 2                      |
| RGBA                                    | RGBA            | UNSIGNED_SHORT_5_5_5_1         | 2                      |
| RGB                                     | RGB             | UNSIGNED_BYTE                  | 3                      |
| RGB                                     | RGB             | UNSIGNED_SHORT_5_6_5           | 2                      |
| LUMINANCE_ALPHA                         | LUMINANCE_ALPHA | UNSIGNED_BYTE                  | 2                      |
| LUMINANCE                               | LUMINANCE       | UNSIGNED_BYTE                  | 1                      |
| ALPHA                                   | ALPHA           | UNSIGNED_BYTE                  | 1                      |

