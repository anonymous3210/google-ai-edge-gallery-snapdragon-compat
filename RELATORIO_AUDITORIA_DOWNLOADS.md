# Auditoria de downloads — Google AI Edge Gallery 1.0.20

Versão auditada: `1.0.20` (`model_allowlists/1_0_20.json`).

A verificação usou requisição HTTP de 1 byte (`Range: bytes=0-0`), sem baixar os modelos completos.

| Modelo | HTTP | Situação | Link efetivo |
|---|---:|---|---|
| Gemma-4-E2B-it | 206 | Disponível; arquivo respondeu corretamente. | [download](https://huggingface.co/litert-community/gemma-4-E2B-it-litert-lm/resolve/b3ca0d2f076785a8f4b2219ddbd2bdb99954eae1/gemma-4-E2B-it.litertlm?download=true) |
| Gemma-4-E4B-it | 206 | Disponível; arquivo respondeu corretamente. | [download](https://huggingface.co/litert-community/gemma-4-E4B-it-litert-lm/resolve/2eee7ac325f20eb8c9ac1d0e972f7c84663062da/gemma-4-E4B-it.litertlm?download=true) |
| EmbeddingGemma-2 | 206 | Disponível; arquivo respondeu corretamente. | [download](https://huggingface.co/litert-community/embeddinggemma-2-740m-litert-lm/resolve/24d962e906c7d332c6428e71c9676855024569e2/embeddinggemma-2-740m.litertlm?download=true) |
| Gemma-3n-E2B-it | 401 | Arquivo existe, mas o repositório é gated; requer token/aceite no Hugging Face. | [download](https://huggingface.co/google/gemma-3n-E2B-it-litert-lm/resolve/c03b6f60b8da6c5400b6838a2cf26420f80c0a01/gemma-3n-E2B-it-int4.litertlm?download=true) |
| Gemma-3n-E4B-it | 401 | Arquivo existe, mas o repositório é gated; requer token/aceite no Hugging Face. | [download](https://huggingface.co/google/gemma-3n-E4B-it-litert-lm/resolve/297ed75955702dec3503e00c2c2ecbbf475300bc/gemma-3n-E4B-it-int4.litertlm?download=true) |
| Gemma3-1B-IT | 401 | Arquivo existe, mas o repositório é gated; requer token/aceite no Hugging Face. | [download](https://huggingface.co/litert-community/Gemma3-1B-IT/resolve/a6306a4e292016480083b73b8dc6f3f939ae04c3/gemma3-1b-it-int4.litertlm?download=true) |
| Qwen2.5-1.5B-Instruct | 206 | Disponível; arquivo respondeu corretamente. | [download](https://huggingface.co/litert-community/Qwen2.5-1.5B-Instruct/resolve/19edb84c69a0212f29a6ef17ba0d6f278b6a1614/Qwen2.5-1.5B-Instruct_multi-prefill-seq_q8_ekv4096.litertlm?download=true) |
| DeepSeek-R1-Distill-Qwen-1.5B | 206 | Disponível; arquivo respondeu corretamente. | [download](https://huggingface.co/litert-community/DeepSeek-R1-Distill-Qwen-1.5B/resolve/2f8b8ee90d8f93b15305b699e8772b277d074a9a/DeepSeek-R1-Distill-Qwen-1.5B_multi-prefill-seq_q8_ekv4096.litertlm?download=true) |
| TinyGarden-270M | 401 | Arquivo existe, mas o repositório é gated; requer token/aceite no Hugging Face. | [download](https://huggingface.co/litert-community/functiongemma-270m-ft-tiny-garden/resolve/aca35636dccadc77499c9843d9ff044b7e06566e/tiny_garden_q8_ekv1024.litertlm?download=true) |
| MobileActions-270M | 401 | Arquivo existe, mas o repositório é gated; requer token/aceite no Hugging Face. | [download](https://huggingface.co/litert-community/functiongemma-270m-ft-mobile-actions/resolve/f752a74080682b379823794defdbbdf8c2663609/mobile_actions_q8_ekv1024.litertlm?download=true) |
| Magic touch | 206 | Disponível; arquivo respondeu corretamente. | [download](https://storage.googleapis.com/mediapipe-models/interactive_segmenter_v2/magic_touch/int8/latest/interactive_segmentation.task) |

## Alterações

- Atualizados os commits fixados para o `HEAD` atual dos repositórios Hugging Face.
- Confirmado via API que cada `modelFile` existe no `HEAD` correspondente.
- A allowlist atualizada foi embutida no APK em `assets/model_allowlists/1_0_20.json` e é priorizada antes da allowlist remota.

## Observação sobre HTTP 401

`401` não é link quebrado nem `404`. Significa que o modelo está protegido/gated no Hugging Face. Isso ocorre em Gemma3-1B, Gemma 3n E2B/E4B, TinyGarden e MobileActions. O usuário precisa autenticar/aceitar os termos no Hugging Face e fornecer o token no app, quando solicitado.

Resultado: **nenhum 404 foi encontrado na allowlist ativa após a atualização**.
