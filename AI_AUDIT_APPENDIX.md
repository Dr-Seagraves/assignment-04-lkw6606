# AI Audit Appendix (Assignment 04)

## Tool(s) Used
- I used the github copiolet only on this assignment. 


## Task(s) Where AI Was Used
error with fetch interest rates- It would not run so I asked the copiolet to help ne find the error.

Error running the assignment014_regression.py

Code troubleshooting- I saw in github there was an autograding error so I pasted the error it gave me into the copiolet so it could help me resolve it. The prompt is listed below.

## Prompt(s) 
- ["help me solve the error that prevented the sucessful run of fetch_interest_rates.py. Reference the file listed, the README.md, and the terminal"]

-"I tried to run assignment04_regression.py and it encourtered an error can you please help me fix it?" and once it answered what the error was I had to type "how do i fix this error?" because it did not give me any solution or tips. 


[Code troubleshooting]- "Igot an error with my code can you help me fix it?" and then I posted the full error 
What error message or traceback are you seeing? Paste the full output.
........F. [100%] =================================== FAILURES =================================== __________________________ test_data_loaded_correctly __________________________ def test_data_loaded_correctly() -> None: """Test that the real REIT annual data can be loaded and has expected structure.""" data_dir = _get_repo_root() / "data" candidates = list(data_dir.glob("REIT_sample_annual_*.csv")) if not candidates: raise FileNotFoundError( f"No REIT_sample_annual_*.csv in {data_dir}. Use REIT_sample_annual_2004_2024.csv." ) data_path = max(candidates, key=lambda p: p.stat().st_mtime) df = pd.read_csv(data_path) required_cols = {"ret12", "div12m_me", "ffo_at_reit", "year"} > assert required_cols.issubset(set(df.columns)), ( f"Missing required columns. Expected {required_cols}, got {set(df.columns)}" ) E AssertionError: Missing required columns. Expected {'ret12', 'ffo_at_reit', 'div12m_me', 'year'}, got {'year', 'age', 'ret', 'comnam', 'div12m_me', 'beta', 'lnmcap', 'ticker', 'permno', 'ffo_at_reit'} E assert False E + where False = <built-in method issubset of set object at 0x7fc426947680>({'age', 'beta', 'comnam', 'div12m_me', 'ffo_at_reit', 'lnmcap', ...}) E + where <built-in method issubset of set object at 0x7fc426947680> = {'div12m_me', 'ffo_at_reit', 'ret12', 'year'}.issubset E + and {'age', 'beta', 'comnam', 'div12m_me', 'ffo_at_reit', 'lnmcap', ...} = set(Index(['year', 'permno', 'ticker', 'comnam', 'age', 'div12m_me', 'ffo_at_reit',\n 'beta', 'lnmcap', 'ret'],\n dtype='str')) E + where Index(['year', 'permno', 'ticker', 'comnam', 'age', 'div12m_me', 'ffo_at_reit',\n 'beta', 'lnmcap', 'ret'],\n dtype='str') = year permno ticker ... beta lnmcap ret\n0 2004 10952 UNII ... -0.239846 12.241140 0.2... 1.100461 13.716664 0.022228\n2629 2024 93419 HPP ... 1.402716 13.494876 -0.604286\n\n[2630 rows x 10 columns].columns tests/test_assignment04.py:144: AssertionError =========================== short test summary info ============================ FAILED tests/test_assignment04.py::test_data_loaded_correctly
- AssertionError: Missing required columns. Expected {'ret12', 'ffo_at_reit',... 1 failed, 9 passed in 23.23s ❌ pytest ::error::Error: Exit with code: 1 and signal: null ::***:: Points 0/50
What command or test did you run to get the error? (e.g., `python assignment04_regression.py` or `pytest`)
pytest
Did this start after a recent change? If so, what did you edit?
Im not sure" 



## Output Summary
- running fetch int rates issue: "The 400 error is coming from a leading space in your FRED API key. The terminal output shows api_key=+c2200..., which indicates the space got URL-encoded. I fixed the script to strip whitespace before making the request.

Change made in fetch_interest_rates.py:91:

Strip whitespace from FRED_API_KEY and env var value to prevent malformed requests.
If you want, you can also remove the leading space in the hardcoded key to keep it clean.

Next steps:

Re-run python fetch_interest_rates.py.
If it still fails, paste the new error output."

for assignment regression error: "Bad Unicode escape in JSON at position 2243 (line 1 column 2244)" then after I asked "how do I fix this error" it responded "I filled in the TODOs that caused the NotImplementedError and the other incomplete parts that would have failed next. The regression now runs, saves outputs, and plots.

Edits made in assignment04_regression.py:101-183:

Implemented estimate_regression() to fit OLS.
Wrote save_regression_summary() to output the summary text.
Completed plot_scatter_with_regression() (scatter + OLS line + R² + axis zoom).
Implemented print_key_results() (coeffs, SEs, t, p, R², N, significance).
Next steps:

Run python assignment04_regression.py again.
If it errors, paste the new terminal output."

for error in github auto grade: "I fixed the failing test by restoring the ret12 column in the data file and made the loader resilient when both ret and ret12 exist (avoids duplicate ret columns). The change in the loader is in assignment04_regression.py:90-97. The data file now includes ret12 again in REIT_sample_annual_2004_2024.csv.
Next step to verify:

Run pytest again to confirm all tests pass."


## Verification & Modifications (Disclose • Verify • Critique)
- **Verify:** I verified by running the script to test and reading carefully what the responses were so I could make sure it understood my prompt. 
- **Critique:** Nothing the AI did was wrong or incomplete from what I can tell.
- **Modify:** I fixed the error with the investments fetch becuase I accidentally put a leading space and the AI allerted me to that. 

## If No AI Tools Used
Write: "No AI tools were used for this assignment."
