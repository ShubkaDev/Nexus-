# Nexus OC — A Custom Android Experience

> "Learning AOSP by building something real."

Nexus OC is a custom Android ROM project based on AOSP Android 16. It's my personal journey into Android internals, with the long-term goal of powering custom devices under a personal brand.

This project is built to be clean, stable, and educational: I'm documenting every step so that other developers can see how a real AOSP-based ROM comes together — from the emulator to real hardware.

---

## Mission

- Master the full AOSP build flow: from `repo sync` to flashing images.
- Create a stable, reproducible base for future custom devices.
- Share knowledge and tooling openly, while keeping core ROM logic under internal development.
- Build responsibly: no clean builds on shared queues, only incremental builds to respect community resources.

---

## Current Stage

| Stage | Status | Notes |
|-------|--------|-------|
| **Stage 1: Emulator** | Active | Building for `aosp_arm64-eng` (generic AOSP/goldfish) |
| **Stage 2: Local Manifests** | In progress | Preparing device trees and patches for custom hardware |
| **Stage 3: Real Devices** | Planned | Ports to custom-branded phones after emulator stability |
| **Stage 4: Release** | Future | Stable images for internal testing and limited distribution |

---

## Tech Stack

- **Base:** AOSP Android 16 (`android-16.0.0_r1`)
- **Build system:** `repo` + `mka` (AOSP Make)
- **Target:** Emulator (`aosp_arm64`) -> future custom hardware
- **CI/CD:** Preparing Crave Devspace automation
- **Storage & Sync:** Local + GitHub for docs/tools; AOSP repos via `repo`

---

## Project Structure (planned)

- `local_manifests/` — device-specific overrides and custom repos
- `patches/` — targeted patches for AOSP components
- `tools/` — helper scripts for sync/build/test
- `docs/` — build instructions, troubleshooting, and notes
- `images/` — screenshots, diagrams, and visual docs (coming soon)

---

## Quick Start (Local Build for Emulator)

These steps are for learning and local testing. For heavy builds, I'll use Crave Devspace once access is approved.

1. **Initialize repo**
   ```bash
   repo init -u https://android.googlesource.com/platform/manifest -b android-16.0.0_r1
   repo sync -j4
   ```

2. **Set up environment**
   ```bash
   source build/envsetup.sh
   ```

3. **Choose target**
   ```bash
   lunch aosp_arm64-eng
   ```

4. **Build**
   ```bash
   mka -j4 aosp_arm64-eng
   ```
   > For a 16 GB RAM machine, `-j4` is a safe default. Adjust based on CPU cores.

5. **Run in emulator**
   Images are located at:
   `out/target/product/aosp_arm64-eng/`

   Launch with:
   ```bash
   ./emulator -system out/target/product/aosp_arm64-eng/system.img
   ```

---

## Contributions

Contributions are welcome in:
- Documentation improvements
- Build helper scripts
- CI/CD templates
- Troubleshooting notes

Core ROM changes and device-specific trees are developed internally at this stage.

If you spot a mistake or have a better way to do something, open an issue or a PR — I'd love to learn from it.

---

## Important Notes

- This is a **personal development project**. No builds for third-party commercial projects are planned.
- On shared build queues (like Crave), **no clean builds** (`make clean`) are performed. Only incremental builds are used to respect queue fairness.
- The name "Nexus OC" is used as a project identity; no trademark claims are made.

---

## License

AOSP source code is licensed under Apache 2.0, BSD, and GPL variants. All custom code in this repository is licensed under **Apache 2.0** unless otherwise noted.

---

## Get in Touch

I'd love to hear your thoughts, questions, or suggestions. You can:
- Open an **issue** on GitHub
- Reach out via **Telegram** or **Discord** (links coming soon)
- Follow the project for updates

---

## Roadmap (High-Level)

- [ ] Emulator build stable and reproducible
- [ ] Local manifests for custom components
- [ ] Crave CI automation template
- [ ] Device tree preparation for custom hardware
- [ ] First internal test images

---

Nexus OC isn't about reinventing Android — it's about understanding it deeply and building something that fits my own vision. Every commit is a step toward that goal.

---
---

# Nexus OC — Кастомный Android-проект (русская версия)

> «Изучаю AOSP, создавая что-то настоящее».

Nexus OC — это проект кастомной прошивки на базе AOSP Android 16. Это мой личный путь вглубь Android с долгой целью: в будущем строить собственные устройства под собственным брендом.

Проект задуман как чистый, стабильный и обучающий: я документирую каждый шаг, чтобы другие разработчики могли увидеть, как из исходников AOSP собирается настоящая прошивка — от эмулятора до реального железа.

---

## Миссия

- Освоить полный цикл сборки AOSP: от `repo sync` до прошивки образов.
- Создать стабильную, воспроизводимую основу для будущих собственных устройств.
- Открыто делиться знаниями и инструментами, оставляя ядро прошивки во внутренней разработке.
- Собирать ответственно: на общих очередях сборки не делаем «чистых» сборок, только инкрементальные — из уважения к ресурсам сообщества.

---

## Текущий этап

| Этап | Статус | Примечания |
|------|--------|------------|
| **Этап 1: Эмулятор** | В работе | Сборка под `aosp_arm64-eng` (generic AOSP/goldfish) |
| **Этап 2: Local Manifests** | В процессе | Готовим device tree и патчи под собственное железо |
| **Этап 3: Реальные устройства** | Запланировано | Портирование на телефоны собственного бренда после стабилизации эмулятора |
| **Этап 4: Релиз** | В будущем | Стабильные образы для внутреннего тестирования и ограниченного распространения |

---

## Технологии

- **База:** AOSP Android 16 (`android-16.0.0_r1`)
- **Система сборки:** `repo` + `mka` (AOSP Make)
- **Цель:** эмулятор (`aosp_arm64`) -> в перспективе собственное железо
- **CI/CD:** готовится автоматизация через Crave Devspace
- **Хранение и синхронизация:** локально + GitHub для документации и инструментов; репозитории AOSP через `repo`

---

## Структура проекта (планируемая)

- `local_manifests/` — манифесты с переопределениями и своими репозиториями
- `patches/` — точечные патчи компонентов AOSP
- `tools/` — вспомогательные скрипты для синхронизации, сборки и тестов
- `docs/` — инструкции по сборке, решения проблем, заметки
- `images/` — скриншоты, схемы и наглядные материалы (скоро)

---

## Быстрый старт (локальная сборка под эмулятор)

Эти шаги — для обучения и локального тестирования. Для тяжёлых сборок буду использовать Crave Devspace после одобрения доступа.

1. **Инициализация repo**
   ```bash
   repo init -u https://android.googlesource.com/platform/manifest -b android-16.0.0_r1
   repo sync -j4
   ```

2. **Настройка окружения**
   ```bash
   source build/envsetup.sh
   ```

3. **Выбор цели**
   ```bash
   lunch aosp_arm64-eng
   ```

4. **Сборка**
   ```bash
   mka -j4 aosp_arm64-eng
   ```
   > Для машины с 16 ГБ ОЗУ `-j4` — безопасное значение по умолчанию. Подстраивайте под количество ядер процессора.

5. **Запуск в эмуляторе**
   Образы находятся в:
   `out/target/product/aosp_arm64-eng/`

   Запуск:
   ```bash
   ./emulator -system out/target/product/aosp_arm64-eng/system.img
   ```

---

## Участие в проекте

Приветствуются вклады в:
- улучшение документации;
- вспомогательные скрипты сборки;
- шаблоны CI/CD;
- заметки по решению проблем.

Изменения ядра прошивки и device tree на данном этапе ведутся внутри проекта.

Если заметили ошибку или знаете способ лучше — откройте issue или PR, буду только рад.

---

## Важные замечания

- Это **личный проект разработки**. Сборки для сторонних коммерческих проектов не планируются.
- На общих очередях сборки (например, Crave) **не выполняются «чистые» сборки** (`make clean`). Используются только инкрементальные сборки — из уважения к очереди.
- Название «Nexus OC» используется как идентификация проекта; претензий на чужие торговые марки нет.

---

## Лицензия

Исходный код AOSP распространяется под лицензиями Apache 2.0, BSD и вариантами GPL. Весь собственный код в этом репозитории — под лицензией **Apache 2.0**, если не указано иное.

---

## Контакты

Буду рад мыслям, вопросам и предложениям:
- откройте **issue** на GitHub;
- напишите в **Telegram** или **Discord** (ссылки скоро появятся);
- следите за проектом, чтобы не пропустить обновления.

---

## Дорожная карта (кратко)

- [ ] Стабильная и воспроизводимая сборка под эмулятор
- [ ] Local manifest для собственных компонентов
- [ ] Шаблон автоматизации сборки на Crave
- [ ] Подготовка device tree под собственное железо
- [ ] Первые внутренние тестовые образы

---

Nexus OC — не про то, чтобы переизобрести Android, а про то, чтобы понять его в глубину и создать что-то, соответствующее моему видению. Каждый коммит — шаг к этой цели.
