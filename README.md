<div align="center">

# SG — Security Groups

### Products & Downloads

**Secure Connections. Privacy. Control.**

A family of applications for personal networking, VPN connections and server management.

**Android · Windows · Linux · SG-Net**

</div>

---

**Навигация:** [Продукты](#продукты) · [SG-Mobile 084 — что нового](#sg-mobile-084--что-нового) · [Загрузки](#загрузки) · [English](#english-overview)

## Продукты

| Продукт | Платформа | Назначение |
| :--- | :--- | :--- |
| **SG-Mobile** | Android | Универсальный VPN-клиент с несколькими сетевыми ядрами, SG-Net и Shadowsocks/Outline |
| **SG-Client** | Windows | Настольный VPN- и proxy-клиент с управлением подключениями, подписками и маршрутизацией |
| **SG-Net** | Server / Clients | Собственный сетевой протокол и серверная инфраструктура с транспортами TLS, WSS и H3/QUIC |
| **SG-Gateway** | Linux Server | Веб-панель для настройки и управления VPN-сервером, клиентами и сетевыми службами |
| **SG-Panel** | Linux Server | Панель для управления Xray, несколькими каналами подключения и серверными узлами |

**SG — Security Groups** объединяет клиентские приложения, сетевые транспорты и серверные инструменты в одну экосистему. Каждый продукт может использоваться самостоятельно, а совместимые компоненты могут работать вместе.

---

## SG-Mobile

**Android · ARM64 · VPN / SOCKS5 · Multi-core**

SG-Mobile — Android-приложение для подключения к собственным и сторонним VPN- и proxy-серверам. Приложение объединяет разные протоколы и сетевые ядра в одном интерфейсе: импорт профилей, подписки, управление подключением, DNS, маршрутизацию и диагностику.

### SG-Mobile 084 — что нового

**Текущая описываемая сборка: 084 FIX6**  
**Версия приложения:** `0.0.110-084-FIX6` · `versionCode 212`  
**Совместимость:** Android 8.0+, `arm64-v8a`

#### 1. Shadowsocks и Outline

- Добавлена поддержка ссылок **`ss://`** и Shadowsocks-профилей.
- Поддерживаются обычные ссылки, Base64-кодирование, импорт по ссылкам и из подписок.
- Добавлен отдельный транспорт на базе **Outline SDK** для Shadowsocks-ссылок с параметром `prefix`.
- Outline-префикс сохраняется как исходная последовательность байтов, включая префиксы с двоичными значениями в URL.
- Обычный Shadowsocks использует Xray; профили, которым необходим Outline `prefix`, направляются через Outline-совместимое ядро.
- Разделены обработка профиля и выбор сетевого движка, чтобы ссылка с `prefix` не запускалась ошибочно как обычный Shadowsocks.
- Исправлены конфигурация Shadowsocks для Xray и тесты импорта подписок.

#### 2. Поддержка SG-Net

В SG-Mobile интегрированы три транспорта SG-Net:

| Транспорт | Тип соединения |
| :--- | :--- |
| **TLS** | Прямое соединение через TLS |
| **WSS** | WebSocket поверх TLS |
| **H3** | HTTP/3 поверх QUIC |

SG-Net работает вместе с остальными протоколами приложения. Поддержка H3 зависит от сетевых условий и доступности UDP на стороне сервера и клиента.

#### 3. Обновлённые сетевые ядра в FIX6

| Компонент | Версия |
| :--- | :--- |
| **Xray / libXray** | `26.10.29` |
| **sing-box** | `1.14.4` |
| **Mihomo** | `1.19.33` |
| **Mieru** | `3.39.0` |
| **Hysteria2** | `2.13.0` |
| **AmneziaWG** | AWG 3.1 |
| **Outline SDK** | `v0.0.23` |

Для sing-box сохранена используемая SG-конфигурация сборки с Naive/Cronet. Hysteria2, AmneziaWG, Outline SDK и SG-Net в FIX6 не заменялись без необходимости.

#### 4. Интерфейс и повседневная работа

В SG-Mobile доступны:

- **VPN/TUN и локальный SOCKS5**, управление запуском и остановкой подключения.
- Импорт профилей и подписок, включая QR-ссылки.
- Отдельные настройки DNS, маршрутизации, GeoIP/GeoSite и IPv4/IPv6.
- Поддержка нескольких сетевых движков в одном приложении.
- Просмотр состояния и диагностика подключений.
- Светлая и тёмные темы, включая **SG Soft** и **Pure Black OLED**.

В линии 084 основное внимание уделено расширению совместимости профилей, подключению SG-Net и Outline, обновлению ядер и сохранению существующих возможностей без переустановки приложения.

#### 5. Обновление приложения

При обновлении SG-Mobile устанавливайте новую версию **поверх существующей**. Не удаляйте приложение ради обновления: при одинаковом идентификаторе приложения и корректной подписи Android сохраняет данные установленной версии.

Для проверки подлинности используйте контрольную сумму SHA-256 опубликованного APK и сведения о выпуске. Файлы ключей и подписи в публичном репозитории не размещаются.

---

## SG-Client

**Windows · Portable · VPN / TUN / System Proxy / Local Proxy**

SG-Client — настольное приложение для Windows, объединяющее несколько сетевых ядер и способов подключения.

**Основные возможности:** импорт ссылок и подписок, управление профилями, TUN и системный прокси, локальный прокси, диагностика, GeoIP/GeoSite, правила маршрутизации и отображение состояния соединения.

Поддерживаются протоколы, реализованные через Xray, sing-box, Mihomo, Mieru и AmneziaWG 3.1. Поддержка транспортов SG-Net зависит от конкретной версии Windows-клиента.

---

## SG-Net

**Server & Client Protocol · TLS · WSS · H3/QUIC**

SG-Net — собственный сетевой протокол и комплекс серверных и клиентских компонентов Security Groups.

- **TLS** — прямой защищённый транспорт.
- **WSS** — транспорт через WebSocket Secure.
- **H3/QUIC** — транспорт через HTTP/3 и UDP.
- Управление клиентами и устройствами, ключами доступа и конфигурациями.
- Интеграция с SG-Mobile и серверной панелью SG-Net.

Транспорты могут различаться по доступности и производительности в зависимости от сети, устройства и настроек сервера.

---

## SG-Gateway

**Linux Server · Web Management**

SG-Gateway — веб-панель для развёртывания и администрирования собственного VPN-сервера.

Серверные подключения, клиенты и устройства, ссылки и подписки, HTTPS, маршрутизация, GeoFiles, состояние служб и обслуживание сервера собраны в едином интерфейсе. Поддерживаемые протоколы и функции зависят от версии SG-Gateway.

---

## SG-Panel

**Linux Server · Xray · Multi-transport**

SG-Panel — отдельный проект серверной панели с управлением несколькими Xray-каналами, профилями и устройствами клиентов. Включает инструменты для HTTPS, маршрутизации, диагностики, обслуживания и управления серверными узлами.

SG-Panel и SG-Gateway — **разные продукты** с собственными версиями и архитектурой.

---

## Загрузки

**Установочные файлы распространяются через Google Cloud Storage.**

| Продукт | Формат | Загрузка |
| :--- | :--- | :--- |
| SG-Mobile | Android APK | Прямая ссылка будет добавлена после публикации проверенного APK в Google Cloud Storage |
| SG-Client | Windows Portable ZIP | Прямая ссылка будет добавлена после публикации |
| SG-Net | Серверный установщик | Прямая ссылка будет добавлена после публикации |
| SG-Gateway | Linux RUN | Прямая ссылка будет добавлена после публикации |
| SG-Panel | Серверный установщик | Прямая ссылка будет добавлена после публикации |

**Важно:** в этом репозитории **нет исходного кода, APK, EXE, ZIP, RUN, ключей, пользовательских конфигураций или бинарных релизов**. Здесь публикуются только описания продуктов, сведения о версиях и ссылки на внешние загрузки.

Точные URL загрузок будут добавляться только после размещения соответствующих объектов в бакете Google Cloud Storage. Рекомендуется проверять SHA-256 перед установкой.

---

## English overview

**SG — Security Groups** is a family of networking applications and server management tools.

- **SG-Mobile (Android):** a multi-core VPN client with Shadowsocks, Outline prefix support and SG-Net TLS/WSS/H3. The highlighted release is **084 FIX6**, with refreshed Xray, sing-box, Mihomo and Mieru cores.
- **SG-Client (Windows):** a portable multi-protocol VPN/proxy client with subscriptions, routing and diagnostics.
- **SG-Net:** a custom networking protocol and server/client stack supporting TLS, WebSocket Secure and HTTP/3 over QUIC.
- **SG-Gateway:** a Linux VPN server management panel.
- **SG-Panel:** a separate Xray-focused Linux control panel with multi-transport management.

**Distribution:** Installers and packages are hosted in Google Cloud Storage. This GitHub repository contains product information only; no source code or distributable binaries.

---

<div align="center">

**SG — Security Groups**

*Secure Connections. Privacy. Control.*

</div>
