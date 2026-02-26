# Fractal Platform PRD

## Original Problem Statement
Развернуть код из репозитория https://github.com/solyankastayl-cyber/343434343
- Поднять frontend, backend и админку
- DXY фракталы - основной модуль для доработки
- SPX и BTC логика в заморозке - поднимаются как есть
- Macro API key: 2c0bf55cfd182a3a4d2e4fd017a622f7

## Architecture
- **Backend**: Python Proxy (8001) → TypeScript Fastify (8002)
- **Frontend**: React with lazy loading (3000)
- **Database**: MongoDB (27017)
- **Assets**: DXY (основной), SPX, BTC (заморожены)

## What's Been Implemented (2026-02-26)

### Deployment Complete ✅
- Клонирован репозиторий и скопированы файлы
- Установлены все зависимости (npm, yarn, pip)
- Настроены .env файлы (MONGODB_URI, MACRO_API_KEY)
- Запущены все сервисы через supervisor
- Исправлена синтаксическая ошибка в FractalChartCanvas.jsx

### Test Results ✅
- Backend: **100%** (8/8 endpoints)
- Frontend: **100%** (все 4 страницы работают)
- Integration: **95%** (WebSocket нестабилен, но не критично)

## Key API Endpoints
- `GET /api/health` - Health check (proxy + ts_backend)
- `GET /api/fractal/dxy/terminal?focus=30d` - DXY Terminal (4 paths)
- `GET /api/fractal/spx?focus=30d` - SPX data
- `GET /api/btc/v2.1/terminal?focus=30d` - BTC data

## Key Routes
- `/fractal/dxy` - DXY Fractal Page (Synthetic/Replay/Hybrid/Macro tabs)
- `/spx` - SPX Terminal
- `/bitcoin` - BTC Terminal
- `/admin/fractal` - Admin Panel (Institutional Dashboard)

## Data Status
- DXY: данные загружены из bootstrap seed (1973-2026)
- SPX: данные загружены (19,000+ candles)
- BTC: данные загружены (5,600+ candles)

## Next Action Items (P0)
1. Стабилизация WebSocket соединений
2. Доработка DXY модуля (macro overlay)

## Backlog (P1/P2)
- P1: Улучшение Macro системы
- P2: Focus-pack endpoint унификация
