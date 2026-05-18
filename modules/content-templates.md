# Content Type Templates

| contentType | Structured Fields |
|---|---|
| investment_research | tickers[], scores{tech,fund,comp}, financials{eps,roe,pe}, institutional{count,pct,ratings} | EXTRACT: 财务→tickers+scores+financials; 机构→institutional; 定性→scores narrative; 缺失标记→⚠️ |
| code_review | language, patterns[], bugs[], perf[], security[], tests{coverage,pct} |
| general | Generic M1 S1 parse |

Match template→structured extraction | else generic