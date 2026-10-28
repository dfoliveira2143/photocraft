# PhotoCraft — funcionalidades e módulos

Última atualização: 2026-10-28.

## Fluxo principal

| Etapa | Entradas | Responsabilidade e dependências | Saídas |
|---|---|---|---|
| Abrir e editar | PSD/PSB, imagens raster e comandos de edição | [psd](../../crates/psd/), [codecs](../../crates/codecs/), [io](../../crates/io/), [doc](../../crates/doc/), [engine](../../crates/engine/) | Documento com camadas, máscaras e histórico |
| Avaliar e produzir saída | Estado editado e parâmetros de saída | [ops](../../crates/ops/), [paint](../../crates/paint/), [algo](../../crates/algo/), [compose](../../crates/compose/), [gpu](../../crates/gpu/), [format](../../crates/format/) | Composição de pixels e documentos/imagens salvos |
| Acesso pelo usuário ou agente | Gestos, argumentos CLI ou chamadas estruturadas | [apps](../../apps/), [engine](../../crates/engine/) e interfaces descritas abaixo | Estado atualizado, resposta ou erro; comportamento detalhado nos contratos |

A tabela mostra o caminho conceitual, não uma garantia de suporte a todos os formatos. APIs, estruturas, unidades, efeitos colaterais e limites ficam na [arquitetura](../architecture.md), nos documentos de assunto e nos módulos indicados.

## Contratos e exemplos de uso

- [development.md](../development.md)
- [contributing.md](../contributing.md)
- [ui-design.md](../ui-design.md)
- [brush-parity.md](../brush-parity.md)
- [smart-filters.md](../smart-filters.md)
- [plugins.md](../plugins.md)
- [control-protocol.md](../control-protocol.md)
- [mcp.md](../mcp.md)

## Inventário de bibliotecas

Responsabilidades resumidas a partir dos manifestos e comentários de módulo do checkout. As dependências listadas são as internas diretas declaradas em `dependencies` (incluindo condicionais); não incluem dependências de teste/build nem expansão de features. O manifesto de cada linha é a fonte exata.

| Módulo / manifesto | Responsabilidade declarada | Dependências internas diretas |
|---|---|---|
| [affinity](../../crates/affinity/Cargo.toml) | Bounded reader for native Affinity documents: archive, object stream and document model | Nenhuma declarada nesta categoria |
| [algo](../../crates/algo/Cargo.toml) | Depth-agnostic, tile-aware CPU image filters (blur, sharpen, noise, distort, stylize) | `photocraft-color`, `photocraft-geom`, `photocraft-raster` |
| [automation](../../crates/automation/Cargo.toml) | MCP server (rmcp) over the PhotoCraft engine, plus a bridge to a running GUI | `photocraft-codecs`, `photocraft-compose`, `photocraft-doc`, `photocraft-engine`, `photocraft-format`, `photocraft-io`, `photocraft-raster` |
| [cms](../../crates/cms/Cargo.toml) | Pure-Rust ICC v2/v4 colour management: profile parsing and writing, transforms, rendering intents, black point compensation | Nenhuma declarada nesta categoria |
| [codecs](../../crates/codecs/Cargo.toml) | Symmetric, depth- and metadata-preserving codecs for flat raster image formats | `photocraft-heif` |
| [color](../../crates/color/Cargo.toml) | Pixel formats, colour models and blend-mode math. | `photocraft-cms` |
| [compose](../../crates/compose/Cargo.toml) | CPU reference compositor. | `photocraft-color`, `photocraft-doc`, `photocraft-geom`, `photocraft-raster`, `photocraft-vector` |
| [doc](../../crates/doc/Cargo.toml) | The PhotoCraft document model: pure data, no rendering, no UI. | `photocraft-color`, `photocraft-geom`, `photocraft-raster` |
| [engine](../../crates/engine/Cargo.toml) | The PhotoCraft engine façade: open documents, history, and the command registry. | `photocraft-algo`, `photocraft-cms`, `photocraft-codecs`, `photocraft-color`, `photocraft-compose`, `photocraft-doc`, `photocraft-format`, `photocraft-geom`, `photocraft-io`, `photocraft-ipp`, `photocraft-ops`, `photocraft-paint`, `photocraft-plugins`, `photocraft-psd`, `photocraft-raster`, `photocraft-text`, `photocraft-vector` |
| [format](../../crates/format/Cargo.toml) | Native .pcraft document bundle: manifest + content-addressed zstd tiles | `photocraft-codecs`, `photocraft-color`, `photocraft-doc`, `photocraft-geom`, `photocraft-raster` |
| [geom](../../crates/geom/Cargo.toml) | Geometry primitives shared by every PhotoCraft crate. | Nenhuma declarada nesta categoria |
| [gpu](../../crates/gpu/Cargo.toml) | GPU compositor (architecture §7.2, milestone M5). | `photocraft-algo`, `photocraft-color`, `photocraft-compose`, `photocraft-doc`, `photocraft-geom`, `photocraft-raster` |
| [heif](../../crates/heif/Cargo.toml) | Optional HEIF/HEIC still-image decoder for PhotoCraft (a thin, panic-guarded wrapper around heic-rs) | Nenhuma declarada nesta categoria |
| [io](../../crates/io/Cargo.toml) | Import/export between photocraft documents and PSD/PSB and flat raster formats | `photocraft-affinity`, `photocraft-algo`, `photocraft-cms`, `photocraft-codecs`, `photocraft-color`, `photocraft-compose`, `photocraft-doc`, `photocraft-format`, `photocraft-geom`, `photocraft-paint`, `photocraft-psd`, `photocraft-raster`, `photocraft-raw`, `photocraft-text`, `photocraft-vector` |
| [ipp](../../crates/ipp/Cargo.toml) | A small IPP client for CUPS (list printers, default printer, print a PDF), pure Rust, no dependencies | Nenhuma declarada nesta categoria |
| [ops](../../crates/ops/Cargo.toml) | Undo/redo history. | `photocraft-doc` |
| [paint](../../crates/paint/Cargo.toml) | Brush engine: Photoshop-grade brushes (computed and sampled tips, Shape Dynamics, Scattering, Texture, Dual Brush, Color Dynamics, Transfer, Brush Pose, Noise, Wet Edges, Build-up, Smoothing) plus the dab machinery shared by the retouching tools. | `photocraft-color`, `photocraft-geom`, `photocraft-raster` |
| [plugins](../../crates/plugins/Cargo.toml) | Sandboxed WebAssembly filter plug-ins: a resource-limited wasmi host for the PhotoCraft plug-in ABI | `photocraft-color`, `photocraft-geom`, `photocraft-raster` |
| [psd](../../crates/psd/Cargo.toml) | Faithful, lossless reader and writer for Adobe Photoshop PSD (v1) and PSB (v2) files | Nenhuma declarada nesta categoria |
| [raster](../../crates/raster/Cargo.toml) | Sparse, copy-on-write tiled surfaces in any `PixelFormat`. | `photocraft-color`, `photocraft-geom` |
| [raw](../../crates/raw/Cargo.toml) | Clean-room, pure-Rust camera raw decoder and developer (DNG, CR2, TIFF/EP raws) | Nenhuma declarada nesta categoria |
| [tablet](../../crates/tablet/Cargo.toml) | Pen tablet pressure, tilt, rotation and eraser end on macOS (AppKit) and Linux X11 (XInput2), and barrel button on Windows | Nenhuma declarada nesta categoria |
| [testkit](../../crates/testkit/Cargo.toml) | Helpers e fixtures para testes; consultar os módulos públicos antes de reutilizar. | Nenhuma declarada nesta categoria |
| [text](../../crates/text/Cargo.toml) | Font database, text shaping/layout (parley) and text-layer rasterization | `photocraft-color`, `photocraft-doc`, `photocraft-geom`, `photocraft-psd`, `photocraft-raster` |
| [ui-egui](../../crates/ui-egui/Cargo.toml) | PhotoCraft's first UI shell, built on egui/eframe. | `photocraft-algo`, `photocraft-cms`, `photocraft-codecs`, `photocraft-color`, `photocraft-compose`, `photocraft-doc`, `photocraft-engine`, `photocraft-format`, `photocraft-geom`, `photocraft-gpu`, `photocraft-io`, `photocraft-paint`, `photocraft-plugins`, `photocraft-raster`, `photocraft-text`, `photocraft-vector` |
| [vector](../../crates/vector/Cargo.toml) | Vector paths, shape layers, strokes and vector masks → anti-aliased coverage and surfaces | `photocraft-color`, `photocraft-doc`, `photocraft-geom`, `photocraft-raster` |

Ao mudar uma entrada, saída ou dependência, atualize primeiro o contrato do módulo e depois esta navegação. [Voltar ao índice](../INDEX.md).
