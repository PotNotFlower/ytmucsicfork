# YTMusik

Неофициальный клиент YouTube Music для Android **без сервисов Google (GMS)**.

Форк [InterTune](https://github.com/ItzSkyeYT/InterTune) → [OuterTune](https://github.com/OuterTune/OuterTune) → [InnerTune](https://github.com/z-huang/InnerTune). Код идентичен апстриму, изменены только имя, идентификатор пакета и версия.

## Совместимость

- Android 7.0+ (minSdk 24), **Android 10 (API 29) — целевая платформа**.
- Google Play Services не нужны: приложение не использует Play Services, Firebase и сервисы Google Play. Аккаунт Google Play не требуется.

## Возможности

Всё, что есть в InterTune:

- потоковое воспроизведение YouTube Music и локальных файлов в одной очереди;
- скачивание треков и офлайн-режим;
- рекомендации-радио на устройстве, учитывающие лайки и пропуски;
- синхронизированные тексты песен, распознавание треков;
- эквалайзер (10 полос, AutoEq), пространственный звук, выравнивание громкости;
- Android Auto, Chromecast / FCast / DLNA;
- без рекламы и трекинга.

## Установка

1. Откройте [Releases](https://github.com/PotNotFlower/ytmucsicfork/releases/latest) и скачайте `YTMusik-*.apk`.
2. Разрешите установку из неизвестных источников и установите APK.

Если релиза ещё нет, тот же APK лежит в **Actions** → **Build YTMusik APK** → последний успешный
запуск, артефакт `ytmusik-apk` (zip с APK внутри).

Имя файла — `YTMusik-<версия>-core-debug-<versionCode>.apk`, в лончере приложение
называется **YTMusik Debug**. APK — отладочная сборка, подписанная ключом CI. Пакет
`com.potnotflower.ytmusik.debug`, поэтому YTMusik ставится рядом с InterTune и официальным
YouTube Music, не заменяя их.

Релиз публикуется автоматически при пуше тега `v*`; сборка занимает около 20 минут.

## Сборка

Нужны JDK 21 и Android SDK 36, NDK `29.0.13113456` и CMake `3.31.6`:

```bash
git clone --recurse-submodules https://github.com/PotNotFlower/ytmucsicfork
cd ytmucsicfork
./gradlew assembleCoreDebug
```

Результат: `app/build/outputs/apk/core/debug/*.apk`.

CI собирает только APK: юнит-тесты апстрима проверяют брендинг и тексты InterTune и в форке не проходят.

## Отличия от апстрима

| | InterTune | YTMusik |
|---|---|---|
| Имя приложения | InterTune | YTMusik (Debug) |
| applicationId | `dev.skye.intertune` | `com.potnotflower.ytmusik` |
| Версия | `0.12.11` | `0.12.11-ytmusik.1` |
| Файл APK | `InterTune-*.apk` | `YTMusik-*.apk` |

## Ограничения

- Встроенные ключи Last.fm привязаны к подписи апстрима, поэтому интеграция Last.fm в форке может не работать.
- Интеграции, которым нужен GMS (например, часть функций Android Auto и каста через Google), без Play Services недоступны.
- Синхронизация и воспроизведение зависят от внутренних API YouTube: при их изменении нужен апстрим-фикс (обновление Submodule `innertubex`).

## Лицензия и благодарности

Проект распространяется по лицензии [GPL-3.0](LICENSE), как и апстрим.

- [InterTune](https://github.com/ItzSkyeYT/InterTune) — непосредственный апстрим
- [OuterTune](https://github.com/OuterTune/OuterTune), [InnerTune](https://github.com/z-huang/InnerTune) — предки
- [NewPipeExtractor](https://github.com/TeamNewPipe/NewPipeExtractor), [innertubex](https://github.com/MetrolistGroup/innertubex), [ffMetadataEx](https://github.com/OuterTune/ffMetadataEx), [taglib](https://github.com/OuterTune/taglib)

Проект не связан с Google и YouTube. Использование может нарушать условия использования YouTube.
