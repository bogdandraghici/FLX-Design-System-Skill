# Colors

FlowX color palettes with 10-step scales, semantic tokens, and dark mode overrides.

## Palettes

CSS variable pattern: `--flowx-{palette}-{shade}`

### Blue

| Shade | Hex       | Variable                |
|-------|-----------|-------------------------|
| 50    | #e6f0fb   | `--flowx-blue-50`      |
| 100   | #b0d1f3   | `--flowx-blue-100`     |
| 200   | #8abbed   | `--flowx-blue-200`     |
| 300   | #549ce5   | `--flowx-blue-300`     |
| 400   | #3389e0   | `--flowx-blue-400`     |
| 500   | #006bd8   | `--flowx-blue-500`     |
| 600   | #005fc0   | `--flowx-blue-600`     |
| 700   | #004c99   | `--flowx-blue-700`     |
| 800   | #003b77   | `--flowx-blue-800`     |
| 900   | #002d5b   | `--flowx-blue-900`     |

### Yellow

| Shade | Hex       | Variable                  |
|-------|-----------|---------------------------|
| 50    | #fff8e7   | `--flowx-yellow-50`      |
| 100   | #ffe9b6   | `--flowx-yellow-100`     |
| 200   | #ffdf92   | `--flowx-yellow-200`     |
| 300   | #fed061   | `--flowx-yellow-300`     |
| 400   | #fec742   | `--flowx-yellow-400`     |
| 500   | #feb913   | `--flowx-yellow-500`     |
| 600   | #e7a811   | `--flowx-yellow-600`     |
| 700   | #b4830d   | `--flowx-yellow-700`     |
| 800   | #8c660a   | `--flowx-yellow-800`     |
| 900   | #6b4e08   | `--flowx-yellow-900`     |

### Green

| Shade | Hex       | Variable                 |
|-------|-----------|--------------------------|
| 50    | #e6f2ef   | `--flowx-green-50`      |
| 100   | #b0d8ce   | `--flowx-green-100`     |
| 200   | #8ac5b6   | `--flowx-green-200`     |
| 300   | #54aa94   | `--flowx-green-300`     |
| 400   | #339980   | `--flowx-green-400`     |
| 500   | #008060   | `--flowx-green-500`     |
| 600   | #007457   | `--flowx-green-600`     |
| 700   | #005b44   | `--flowx-green-700`     |
| 800   | #004635   | `--flowx-green-800`     |
| 900   | #003628   | `--flowx-green-900`     |

### Orange

| Shade | Hex       | Variable                  |
|-------|-----------|---------------------------|
| 50    | #fff0e8   | `--flowx-orange-50`      |
| 100   | #fed1b9   | `--flowx-orange-100`     |
| 200   | #febb97   | `--flowx-orange-200`     |
| 300   | #fe9c67   | `--flowx-orange-300`     |
| 400   | #fd8949   | `--flowx-orange-400`     |
| 500   | #fd6b1c   | `--flowx-orange-500`     |
| 600   | #e66119   | `--flowx-orange-600`     |
| 700   | #b44c14   | `--flowx-orange-700`     |
| 800   | #8b3b0f   | `--flowx-orange-800`     |
| 900   | #6a2d0c   | `--flowx-orange-900`     |

### Red

| Shade | Hex       | Variable               |
|-------|-----------|------------------------|
| 50    | #fde9e6   | `--flowx-red-50`      |
| 100   | #f7bab0   | `--flowx-red-100`     |
| 200   | #f4998a   | `--flowx-red-200`     |
| 300   | #ee6b54   | `--flowx-red-300`     |
| 400   | #eb4e33   | `--flowx-red-400`     |
| 500   | #e62200   | `--flowx-red-500`     |
| 600   | #d11f00   | `--flowx-red-600`     |
| 700   | #a31800   | `--flowx-red-700`     |
| 800   | #7f1300   | `--flowx-red-800`     |
| 900   | #610e00   | `--flowx-red-900`     |

### Neutrals

| Shade | Hex       | Variable                    |
|-------|-----------|------------------------------|
| 50    | #f7f8f9   | `--flowx-neutrals-50`      |
| 100   | #e3e8ed   | `--flowx-neutrals-100`     |
| 200   | #cbd1db   | `--flowx-neutrals-200`     |
| 300   | #a6b0be   | `--flowx-neutrals-300`     |
| 400   | #8390a2   | `--flowx-neutrals-400`     |
| 500   | #64748b   | `--flowx-neutrals-500`     |
| 600   | #5b6a7e   | `--flowx-neutrals-600`     |
| 700   | #475263   | `--flowx-neutrals-700`     |
| 800   | #2a313a   | `--flowx-neutrals-800`     |
| 900   | #1d232c   | `--flowx-neutrals-900`     |

### Grays

| Shade | Hex       | Variable                 |
|-------|-----------|--------------------------|
| 50    | #ffffff   | `--flowx-grays-50`      |
| 900   | #000000   | `--flowx-grays-900`     |

## Semantic Tokens (Light Mode)

| Token                | Alias          | Hex       |
|----------------------|----------------|-----------|
| surface-primary      | grays-50       | #ffffff   |
| surface-secondary    | neutrals-50    | #f7f8f9   |
| surface-tertiary     | neutrals-100   | #e3e8ed   |
| text-primary         | neutrals-900   | #1d232c   |
| text-secondary       | neutrals-500   | #64748b   |
| text-disabled        | neutrals-300   | #a6b0be   |
| border-default       | neutrals-200   | #cbd1db   |
| border-strong        | neutrals-400   | #8390a2   |
| interactive-default  | blue-500       | #006bd8   |
| interactive-hover    | blue-600       | #005fc0   |
| success              | green-500      | #008060   |
| warning              | yellow-500     | #feb913   |
| error                | red-500        | #e62200   |
| info                 | blue-500       | #006bd8   |

## Dark Mode Overrides

| Token              | Alias          | Hex       |
|--------------------|----------------|-----------|
| background         | neutrals-900   | #1d232c   |
| foreground         | neutrals-50    | #f7f8f9   |
| primary            | blue-400       | #3389e0   |
| destructive        | red-400        | #eb4e33   |
| card               | neutrals-800   | #2a313a   |
| muted              | neutrals-700   | #475263   |
| muted-foreground   | neutrals-400   | #8390a2   |
| border             | neutrals-700   | #475263   |
| ring               | blue-400       | #3389e0   |
