# Google AI Edge Gallery — compatibilidade Android 11 / Snapdragon 7xx

**Repositório analisado:** `google-ai-edge/gallery`

**Commit analisado:** `2742d5c8852e9d329411e9b2a08ba918dbf08cc8`

## Conclusão

A versão oficial do código define `minSdk = 31`, portanto exige Android 12. Para o Galaxy A71 com Android 11 (API 30), o APK oficial não é instalável. Foi feita uma variante alterando somente o mínimo para `minSdk = 30`.

A variante **compilou com sucesso** e o APK declara `sdkVersion: 30`.

Não existe no código uma restrição geral para Snapdragon 8xxx/8 Gen 1. O código aceita CPU/GPU conforme a configuração do modelo. Há uma filtragem específica para modelos **NPU-only**, usando `Build.SOC_MODEL`; isso não bloqueia os modelos CPU/GPU do Snapdragon 710/730. Os modelos ainda dependem de RAM e do suporte real do backend LiteRT-LM.

## Evidências do APK

- Pacote: `com.google.aiedge.gallery`
- Versão: `1.0.20` / versionCode `46`
- Compile SDK: 37.0
- Target SDK: 37
- Mínimo no APK gerado: **API 30 (Android 11)**
- Bibliotecas nativas presentes: `arm64-v8a`, `armeabi-v7a`, `x86` e `x86_64`
- A Activity principal é `com.google.ai.edge.gallery.MainActivity`
- Tamanho: 265.588.470 bytes
- SHA-256: `b02125a5f6941a03221cf22174a014ce00b3ddcec6c17da6ccf30bf9c60f04ca`

O Snapdragon 710/730 normalmente usa `arm64-v8a`, ABI presente no APK. A presença da ABI garante instalação/carregamento nativo, mas não garante que cada modelo rode bem em GPU: isso precisa ser validado no aparelho físico.

## Build executado

```bash
cd Android/src
export ANDROID_HOME=/home/ubuntu/android-sdk
export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
./gradlew assembleDebug --no-daemon --stacktrace
```

Resultado: `BUILD SUCCESSFUL`.

## Teste prático no Linux x86_64

Foi criado um AVD Android 11 `google_apis;x86_64` e o teste tentou iniciar o emulador, instalar o APK e abrir a Activity.

O teste não chegou à instalação porque o sandbox não expõe aceleração KVM:

```text
ERROR | x86_64 emulation currently requires hardware acceleration!
CPU acceleration status: /dev/kvm is not found
```

Isso é uma limitação do ambiente Linux de execução, não um crash do aplicativo. Portanto, não é correto declarar que a Activity passou no emulador; o que foi validado foi a compilação, o manifesto, as ABIs e a configuração do APK.

## Limitações conhecidas

1. Android 11 não oferece as APIs/serviços de IA do Google que dependem de Android 12+; recursos baseados em AI Core podem ficar indisponíveis.
2. Modelos grandes têm requisitos explícitos de RAM: por exemplo, modelos de 1B/1.5B aparecem com requisito de aproximadamente 6 GB; modelos Gemma maiores exigem 8–12 GB.
3. GPU/CPU é selecionável nos modelos que declaram ambos. NPU-only continua dependente do SoC suportado e não deve ser “forçado” por uma simples recompilação.
4. A configuração local de Hugging Face ainda precisa de credenciais próprias para baixar modelos, conforme `DEVELOPMENT.md`.

## Alteração realizada

Arquivo: `Android/src/app/build.gradle.kts`

```kotlin
// Android 11 (API 30) is supported by the target Galaxy A71 use case.
minSdk = 30
```

Nenhum filtro de Snapdragon foi removido e nenhum modelo NPU foi falsamente habilitado.
