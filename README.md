# Global Stock Analyzer

A comprehensive stock analysis platform combining Streamlit web interface, REST API backend, and React components for global dividend stock screening.

## Features

### Core Functionality
- **Global Market Screening**: Screen stocks across 22+ international exchanges
- **Advanced Filtering**: 6-criteria dividend stock screening with comprehensive validation
- **Hidden Champion Recommendations**: Expert-curated stock recommendations when screening finds no results
- **Growth Potential Analysis**: 3-year projection metrics with 5x-100x opportunity targeting
- **Real-time Data**: TradingView and Yahoo Finance integration for live market data

### Technical Features
- **Professional UI**: Streamlit-based interface with custom styling and responsive design
- **Backend API**: FastAPI REST endpoints for data management and refresh services
- **Automated Notifications**: Email alerts and real-time badge notifications for qualification changes
- **Data Persistence**: SQLite database for tracking stock history and user preferences
- **Multi-threaded Processing**: Parallel stock validation with progress tracking

## Screening Criteria

The platform uses rigorous 6-criteria filtering:

1. **Free Cash Flow**: > $0 (annual)
2. **Dividend Yield**: ≥ 5% (user-configurable 0-20%)
3. **P/E Ratio**: ≤ 8 (user-configurable 1-50)
4. **Trading Volume**: ≥ 100M shares OR USD notional (user-configurable)
5. **Company Age**: ≥ 3 years (estimated from financial reports)
6. **Stock Price**: < $100 (user-configurable 1-1000)

## Hidden Champion Database

When screening finds no results, the system provides expert-curated recommendations:

- **UnitedHealth (UNH)**: Healthcare sector leader trading at 50%+ discount
- **Merck (MRK)**: Most undervalued pharma stock with strong pipeline
- **Alphabet (GOOG)**: AI/Waymo assets with quantum computing research
- **Verizon (VZ)**: 6.79% dividend yield with 5G infrastructure
- **Home Depot (HD)**: Blue chip with housing market recovery catalyst

## Installation

1. Clone the repository:
```bash
git clone https://github.com/cesaranogilbert/global-stock-analyzer.git
cd global-stock-analyzer
```

2. Install dependencies:
```bash
pip install alpha-vantage>=3.0.0 aiosqlite>=0.21.0 apscheduler>=3.11.0 fastapi>=0.116.1 finnhub-python>=2.4.24 numpy>=2.3.2 pandas>=2.3.1 plotly>=6.2.0 pydantic>=2.11.7 python-multipart>=0.0.20 requests>=2.32.4 schedule>=1.2.2 sendgrid>=6.12.4 streamlit>=1.47.1 streamlit-autorefresh>=1.0.1 tradingview-screener>=3.0.0 trafilatura>=2.0.0 uvicorn>=0.35.0 yfinance>=0.2.65
```

3. Configure Streamlit:
```bash
mkdir .streamlit
echo '[server]
headless = true
address = "0.0.0.0"
port = 5000' > .streamlit/config.toml
```

4. Run the application:
```bash
streamlit run app.py --server.port 5000
```

## Usage

### Dividend Screening
1. Navigate to the main page
2. Select market region or "All Markets" for global screening
3. Adjust screening criteria using the filter panel
4. Click "Screen" to run comprehensive analysis
5. View results in card or table format
6. Analyze individual stocks with detailed metrics

### Growth Potential Analysis
1. Go to "Growth Potential" page
2. Filter by sector and risk tolerance
3. View 3-year growth projections
4. Explore 5x-100x opportunity candidates

### Hidden Champion Recommendations
- Automatically displayed when screening finds no qualifying stocks
- Includes real market data and expert analysis
- Interactive features for detailed analysis and charting

## Architecture

### Frontend
- **Framework**: Streamlit with custom CSS styling
- **Components**: Enhanced filter panels, color-coded KPI cards, dual view modes
- **Visualization**: Plotly charts and TradingView widgets
- **State Management**: Session-based filtering and analysis storage

### Backend
- **API Server**: FastAPI with background scheduler
- **Data Sources**: TradingView (primary), Yahoo Finance (validation)
- **Processing**: Multi-threaded stock validation with up to 1000 stocks per region
- **Database**: SQLite for history tracking and user preferences

### Key Files
- `app.py`: Main Streamlit application
- `growth_potential_page.py`: Growth analysis engine
- `backend_stock_filter.py`: Core filtering logic
- `api_server.py`: REST API endpoints
- `data_refresh_service.py`: Automated data updates
- `notification_system.py`: Email and UI notifications

## API Endpoints

- `GET /api/refresh/{region}`: Trigger manual data refresh
- `GET /api/changes/{region}`: Get recent qualification changes
- `GET /api/preferences/{user_id}`: User preference management
- `GET /api/statistics`: System performance metrics

## Configuration

### Environment Variables
- `SENDGRID_API_KEY`: For email notifications (optional)

### Customization
- Adjust screening criteria in the UI filter panel
- Modify hidden champion database in `app.py`
- Configure refresh intervals in `api_server.py`
- Customize notification settings in `notification_system.py`

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Disclaimer

This software is for educational and research purposes only. Always conduct your own research and consult with qualified financial advisors before making investment decisions. Past performance does not guarantee future results.