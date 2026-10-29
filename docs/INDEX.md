# PhotoCraft — índice de documentação

Última atualização: 2026-10-28.

Ponto de entrada para retomar o projeto sem depender do histórico do chat. Esta base é versionada; `plan/` e `log/`, quando presentes, são apenas material local complementar.

## Roteiro de leitura

1. Leia [AGENTS.md](../AGENTS.md) e [manutenção da base](agent-guide/maintenance.md).
2. Consulte [visão geral](agent-guide/overview.md) e [funcionalidades](agent-guide/features.md).
3. Leia [contexto e pendências](agent-guide/context.md), depois o documento do módulo afetado.
4. Antes de alterar arquivos, consulte [padrões](agent-guide/standards.md) e [operação](agent-guide/operations.md).

## Fontes principais

| Assunto | Fonte única para o detalhe |
|---|---|
| Apresentação do produto | [README](../README.md) |
| Regras obrigatórias e permissões | [AGENTS](../AGENTS.md) |
| Arquitetura e relações entre módulos | [Arquitetura](architecture.md) |
| Estágio e histórico público | [ROADMAP](../ROADMAP.md) |
| Trabalho pendente priorizado | [Lacunas](gaps.md) |
| Marcos e foco atual | [Roadmap detalhado](roadmap.md) |
| Cobertura e evidências | [Avaliação de paridade](target-app-parity.md) |

Os guias são mapas de navegação, não novas cópias dos contratos técnicos. Números de cobertura e status permanecem nas fontes acima. A existência de um módulo ou comando não comprova paridade completa.

## Referências por assunto

- [Batch output naming](batch-naming.md)
- [Brush and painting parity](brush-parity.md)
- [Camera Raw histogram and scopes](camera-raw-histogram.md)
- [Camera Raw preview navigation](camera-raw-zoom.md)
- [Color selection and screen sampling](color-picker.md)
- [Context-menu inventory and parity contract](context-menu-inventory.md)
- [Context-menu parity contract](context-menu-parity.md)
- [Contributing](contributing.md)
- [Contributors in the About window](contributors.md)
- [Control protocol](control-protocol.md)
- [Implementation decisions](decisions.md)
- [Deflate backend comparison](deflate-zlib-rs-performance.md)
- [Development guide](development.md)
- [PhotoCraft: egui 0.37 migration plan](egui-037-migration-plan.md)
- [File-format parity](file-format-parity.md)
- [Five imaging algorithms: measured CPU performance](five-algorithm-performance.md)
- [PostScript font resolution](font-resolution.md)
- [GPU stack prefix reuse](gpu-composite-reuse.md)
- [Hardware parity](hardware-parity.md)
- [Iris Blur computation (2026-10-10)](iris-blur-performance.md)
- [Krita documents](kra.md)
- [Spanish terminology and dynamic UI labels](localization-es.md)
- [Italian terminology and dynamic UI labels](localization-it.md)
- [Korean terminology and dynamic UI labels](localization-ko.md)
- [Localization parity](localization-parity.md)
- [Russian terminology and dynamic UI labels](localization-ru.md)
- [Simplified Chinese catalog](localization-zh-hans.md)
- [UI localisation and live language switching](localization.md)
- [MCP conventions](mcp.md)
- [Nikon D5100 NEF development](nikon-nef-development.md)
- [Exact octagonal mask shifts](octagonal-mask-performance.md)
- [Oil Paint performance](oil-paint-performance.md)
- [OpenRaster documents](ora.md)
- [Photoshop menu parity](parity-checklist.md)
- [Paint.NET documents](pdn.md)
- [Crystallize and Pointillize performance](pixelate-cell-performance.md)
- [Facet and Color Halftone performance](pixelate-performance.md)
- [Plug-ins: the WebAssembly plug-in API (ABI v1)](plugins.md)
- [Printing](printing.md)
- [Proximity Match search and memory](proximity-match-performance.md)
- [PSD pixel buffer allocation](psd-interleave-performance.md)
- [Quick Selection stroke performance](quick-selection-performance.md)
- [Radial Blur sampler optimization](radial-blur-performance.md)
- [Release playbook](release-playbook.md)
- [Releasing PhotoCraft](releasing.md)
- [PhotoCraft scorecard](scorecard.md)
- [Content-Aware Scale performance](seam-carving-performance.md)
- [Selection distance transforms](selection-distance-performance.md)
- [Shape stroke options](shape-strokes.md)
- [Smart Filters in the Layers panel](smart-filters.md)
- [Sparse raster reads](sparse-raster-reads-performance.md)
- [Text rasterization: what a type render costs](text-raster-performance.md)
- [Tilt-Shift computation (2026-10-10)](tilt-shift-performance.md)
- [UI design system](ui-design.md)
- [Dialogs](ui-dialogs.md)
- [UI parity: tools, handles, modifiers and feel](ui-parity.md)
- [Unsharp Mask performance](unsharp-mask-performance.md)
- [Windows native-save durability](windows-save-durability.md)
- [GIMP XCF documents](xcf.md)
- [Native save writer reuse](zstd-workspaces-performance.md)

- [Creative Workshop: origem, identidade e publicação](branding.md)
