# Changelog

Значимые изменения proto-схемы Simple API.

## v3 — 2026-06-16

### Добавлено
- `Event.LegalRu.VAT`: ставка НДС 22% (`VAT_22`).

### Изменено
- ⚠️ Во все файлы добавлен `package v3;` — меняются полные имена типов
  и пространство имён в сгенерированном коде; клиентов перегенерировать.
- ⚠️ Вложенные типы перенесены внутрь родителей: `EventStatus`,
  `SmartTicketSetting`, `Deal`, `LegalRu`, `TicketSet` → в `Event`;
  `TicketStatus` → в `Seat`; `ModType` → в `Mod`. Полные имена типов
  и имена сгенерированных классов изменились.
- ⚠️ `Mod.ModType` перенумерован: добавлен `UNKNOWN = 0`, `PROMOTION`
  теперь `= 1` (было `0`) — несовместимо на уровне wire-формата.

### Удалено
- ⚠️ Top-level enum'ы `EventStatus`, `TicketStatus`, `SmartTicketSetting`,
  `ModType` — перенесены внутрь сообщений (см. «Изменено»).
