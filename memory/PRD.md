# Fractal Platform PRD v2

## Original Problem Statement
Развернуть код из репозитория https://github.com/solyankastayl-cyber/343434343
- DXY фракталы - основной модуль для доработки
- SPX и BTC логика в заморозке
- Macro API key: 2c0bf55cfd182a3a4d2e4fd017a622f7

## Architecture (2026-02-27)

### Backend Stack
- **Python Proxy** (8001) → **TypeScript Fastify** (8002)
- **MongoDB** (27017) for data storage
- **FRED API** integration for macro data

### Frontend Stack
- **React** with lazy loading
- **Canvas** for chart rendering
- **WebSocket** for real-time updates

### Hierarchy of Layers
1. **Synthetic** = ModelForecast(current_state) — pure AI model
2. **Replay** = BestHistoricalMatchPath — historical anchor
3. **Hybrid** = w1 * Synthetic + w2 * Replay — stabilized blend
4. **Macro** = Hybrid + MacroBiasAdjustment — context correction

## What's Been Implemented (2026-02-27)

### Deployment Complete ✅
- Cloned repository and configured environment
- Set up FRED_API_KEY and MACRO_API_KEY
- Fixed FractalChartCanvas.jsx syntax errors
- Removed 7d marker for 365D horizon

### DXY Page Architectural Rebuild ✅
New layout following blueprint:
1. **FORECAST CORE** - 70% Chart | 30% Summary Panel
2. **FRACTAL ENGINE BREAKDOWN** - Historical Anchor + Hybrid Construction
3. **MACRO LAYER** - Regime State + Macro Impact + Macro Drivers
4. **OUTCOMES + RISK** - Distribution + Risk Context
5. **FRACTAL ANALYSIS + TOP MATCHES** - Compact tables
6. **SYSTEM STATUS** - Phase/Context info

### New Components Created
- `/app/frontend/src/components/fractal/ForecastSummaryPanel.jsx`
- `/app/frontend/src/components/fractal/FractalEngineBreakdown.jsx`
- `/app/frontend/src/components/fractal/MacroLayerPanel.jsx`
- `/app/frontend/src/components/fractal/OutcomesRiskPanel.jsx`

### Macro Integration ✅
- 8 FRED series loaded (FEDFUNDS, CPI, UNRATE, etc.)
- scoreSigned = -0.069 (EASING regime)
- Macro adjustment visible: Hybrid vs Macro difference ~0.18%

## Key API Endpoints
- `GET /api/health` - Health check
- `GET /api/fractal/dxy/terminal?focus=30d` - DXY Terminal
- `GET /api/fractal/spx?focus=30d` - SPX data
- `GET /api/dxy-macro-core/score` - Macro score
- `GET /api/ae/terminal` - AE State

## Key Routes
- `/fractal/dxy` - DXY Fractal Page (NEW LAYOUT)
- `/spx` - SPX Terminal
- `/bitcoin` - BTC Terminal
- `/admin/fractal` - Admin Panel

## Data Status
- DXY: 13,366 candles (1973-2026)
- SPX: 19,000+ candles
- BTC: 5,600+ candles
- FRED: 8 macro series loaded

## Next Action Items (P0)
1. Test new layout with different horizons (7D, 90D, 180D, 365D)
2. Fine-tune Macro impact coefficient (0.03 → 0.05)
3. Load remaining FRED series

## Backlog (P1/P2)
- P1: WebSocket stabilization
- P1: Regime timeline mini-chart
- P2: Scenario influence map
