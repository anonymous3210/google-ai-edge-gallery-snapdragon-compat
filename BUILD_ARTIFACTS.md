# Build e artefatos

Este repositório inclui o código-fonte completo, o Gradle Wrapper e as instruções de compilação. O APK compilado é publicado como asset do GitHub Release porque o GitHub rejeita arquivos individuais acima de 100 MB no Git comum.

## Compilar do zero

Linux/macOS:

```bash
cd Android/src
./gradlew assembleDebug
```

Windows:

```bat
cd Android\src
gradlew.bat assembleDebug
```

O APK será gerado em `Android/src/app/build/outputs/apk/debug/app-debug.apk`.

## APK pronto

Baixe o APK na seção **Releases** deste repositório. O checksum correspondente está em `artifacts/SHA256SUMS.txt`.

Requisitos: JDK 21 com `javac`, Android SDK com `platforms;android-37.0`, `build-tools;37.0.0` e `platform-tools`. O Gradle Wrapper baixa automaticamente o Gradle e as dependências na primeira compilação. O arquivo local `Android/src/local.properties` deve apontar para o SDK e não é versionado.
