# AI-Assisted Blood Glucose Test Result Analysis System
## Windows 11 සඳහා ආරම්භක මාර්ගෝපදේශය

මෙය HNDIT1052 ICT Project සඳහා සාදන අධ්‍යාපනික prototype එකකි. Python, Streamlit, Plotly, Pandas, OpenAI Responses API සහ ReportLab භාවිත කරයි.

## ඇතුළත් Features
- FPG, Random glucose, 2-hour OGTT, HbA1c සහ Other test සඳහා manual data entry
- Test date, value, unit සහ laboratory reference range ඇතුළත් කිරීම
- එකම test type සහ unit ඇති ප්‍රතිඵල සඳහා වෙනම trend graphs
- CSV download
- OpenAI API මඟින් English educational report
- AI report TXT ලෙසත් graphs සමඟ PDF ලෙසත් download කිරීම
- API key source code එකේ නොතැබීම
- AI/API failure සඳහා error handling

## 1. Python install කරන්න
1. https://www.python.org/downloads/windows/ වෙත යන්න.
2. Python 3.11 හෝ 3.12 install කරන්න.
3. Installer එකේ **Add python.exe to PATH** tick කරන්න.
4. Install වූ පසු Windows Terminal හෝ Command Prompt එක වසා නැවත විවෘත කරන්න.
5. මේ command එක run කරන්න:
   ```powershell
   py --version
   ```
   Python version එක පෙන්විය යුතුය.

## 2. Project folder එක extract කරන්න
ZIP file එක right-click → **Extract All** කරන්න. Extract කළ folder එකේ `app.py`, `requirements.txt`, `README_SI.md` තිබිය යුතුය.

## 3. Terminal එකෙන් folder එකට යන්න
File Explorer එකෙන් project folder එක open කරන්න. Address bar එකට `cmd` type කර Enter ඔබන්න. එවිට ඒ folder එකේ terminal එක open වේ.

## 4. Virtual environment එක හදන්න
පහත commands එකින් එක run කරන්න:

```powershell
py -m venv .venv
```

```powershell
.venv\Scripts\activate
```

Terminal එකේ ඉදිරියෙන් `(.venv)` පෙනිය යුතුය.

## 5. Packages install කරන්න

```powershell
python -m pip install --upgrade pip
```

```powershell
pip install -r requirements.txt
```

Internet speed අනුව මෙයට මිනිත්තු කිහිපයක් ගත විය හැක.

## 6. OpenAI API key සකස් කරන්න
1. OpenAI Platform හි API key එකක් සාදන්න: https://platform.openai.com/api-keys
2. API usage සඳහා billing/credits සහ project access සකස් වී ඇති බව බලන්න. ChatGPT subscription එක API credits ලෙස ස්වයංක්‍රීයව භාවිත නොවේ.
3. Project folder එකේ `.env.example` file එක copy කර එහි නම `.env` ලෙස වෙනස් කරන්න.
4. `.env` file එක Notepad එකෙන් open කර `OPENAI_API_KEY=put_your_api_key_here` හි value එක ඔබගේ key එකෙන් වෙනස් කරන්න.
5. `.env` file එක කිසිවෙකුට share කරන්න එපා. GitHub වෙත upload කරන්නත් එපා. `.gitignore` එකෙන් එය exclude කර ඇත.

උදාහරණය (මෙය සැබෑ key එකක් නොවේ):
```text
OPENAI_API_KEY=sk-your-own-secret-key
OPENAI_MODEL=gpt-5.5
```

Model access වෙනස් විය හැකි නිසා ඔබගේ API project එකට ලබාගත හැකි model එක භාවිත කරන්න. Model error එකක් ලැබුණොත් sidebar එකේ OpenAI model field එක වෙනස් කළ හැක.

## 7. App එක run කරන්න

```powershell
streamlit run app.py
```

Browser එකක් ස්වයංක්‍රීයව open විය යුතුය. නොවුනොත් terminal එකේ පෙන්වන local URL එක browser එකට copy කරන්න (සාමාන්‍යයෙන් `http://localhost:8501`).

## 8. පළමු test එක
- Test type එක තෝරන්න.
- Test date එක තෝරන්න.
- Value එකක් ඇතුළත් කරන්න.
- Unit එක තෝරන්න.
- Reference range එක තිබේ නම් laboratory report එකේ සඳහන් ආකාරයටම ඇතුළත් කරන්න.
- **Add result** ඔබන්න.
- Graph එක බලන්න.
- AI report අවශ්‍ය නම් **Generate report with OpenAI** ඔබන්න.
- Report එක review කර TXT හෝ PDF download කරන්න.

Demo එකට synthetic data පමණක් භාවිත කරන්න. එකිනෙකට වෙනස් test types හෝ units එකම trend එකක එකතු නොකරයි.

## 9. නවත්වන්නේ / නැවත අරඹන්නේ කොහොමද?
Terminal එකේ `Ctrl + C` ඔබන්න. නැවත අරඹන විට project folder එකේ terminal open කර:

```powershell
.venv\Scripts\activate
streamlit run app.py
```

## Troubleshooting
- **`py` is not recognized**: Python නැවත install කර Add Python to PATH tick කර තිබේද බලන්න; terminal එක නැවත open කරන්න.
- **`streamlit` is not recognized**: `.venv` activate කර `pip install -r requirements.txt` නැවත run කරන්න.
- **API key missing / authentication error**: `.env` නම හරියටද, key එක සම්පූර්ණද, එය revoke වී නැද්ද බලන්න. `.env.txt` ලෙස වැරදිව save වී නැද්ද බලන්න.
- **Model not found / access error**: API project එකට access ඇති model name එක sidebar එකේ දාන්න.
- **Quota / billing / 429 error**: Platform billing, project budget සහ rate limits පරීක්ෂා කරන්න. නැවත නැවත click කිරීමෙන් ගාස්තු හෝ rate limit ගැටලු ඇති විය හැක.
- **PDF error**: `pip install -r requirements.txt` නැවත run කර app එක restart කරන්න.
- **Port busy**: Streamlit පෙන්වන වෙනත් local port එක භාවිත කරන්න.

## Privacy සහ ආරක්ෂාව
- OpenAI වෙත දත්ත යවන්නේ **Generate report with OpenAI** ඔබන විට පමණි.
- නම, NIC, ලිපිනය, දුරකථන අංකය වැනි identifying details ඇතුළත් නොකරන්න.
- API key එක source code එකට hard-code නොකරන්න.
- මෙම prototype එක authentication හෝ multi-user production security ලබා නොදේ.
- AI output එකේ වැරදි තිබිය හැක; එය වෛද්‍ය තීරණ සඳහා භාවිත නොකරන්න.

## සීමා
- මෙය diagnosis හෝ treatment system එකක් නොවේ.
- Laboratory reference ranges පරිශීලකයා විසින් ඇතුළත් කරන දත්තය; ඒවා ස්වයංක්‍රීයව validate කරන්නේ නැත.
- OCR, patient login, cloud database, clinical validation සහ clinician dashboard මෙම පළමු version එකට ඇතුළත් නොවේ.
- Supervisor ගේ feedback අනුව project scope සහ final report එක වෙනස් කළ යුතු විය හැක.

## Official API reference
- OpenAI API quickstart: https://developers.openai.com/api/docs/quickstart
- OpenAI Python library: https://developers.openai.com/api/reference/python


## 10. Phone එකෙන් Internet හරහා open කිරීම (Streamlit Community Cloud)

මෙම app එක mobile browser එකකින් භාවිත කළ හැකි web app එකක්. Phone එකෙන් ඕනෑම තැනකින් open කිරීමට app එක online deploy කළ යුතුයි. Laptop එකේ `localhost` link එක පමණක් phone එකෙන් සාමාන්‍යයෙන් විවෘත කළ නොහැක.

### A. GitHub වෙත project එක upload කරන්න
1. GitHub account එකක් තිබිය යුතුයි: https://github.com
2. නව repository එකක් සාදන්න. උදා: `ai-blood-glucose-analysis`
3. ZIP එක extract කර ඇති project files upload කරන්න.
4. `.env` file එක upload නොකරන්න. API key එක කිසිම අවස්ථාවක repository එකට දාන්න එපා.
5. `.streamlit/config.toml` file එකත් repository එකට ඇතුළත් කරන්න.

### B. Streamlit Community Cloud වෙත deploy කරන්න
1. https://share.streamlit.io වෙත ගොස් GitHub සමඟ sign in කරන්න.
2. **Create app** තෝරන්න.
3. Repository, branch සහ main file path `app.py` තෝරන්න.
4. App settings / Secrets කොටසට ගොස් පහත ආකාරයේ secrets ඇතුළත් කරන්න:

```toml
OPENAI_API_KEY = "ඔයාගේ_API_KEY_එක"
OPENAI_MODEL = "gpt-5.5"
```

5. Deploy කරන්න. Build සාර්ථක නම් Streamlit විසින් online URL එකක් ලබාදෙයි.
6. ඒ URL එක Android phone එකේ Chrome වැනි browser එකෙන් open කරන්න. කැමති නම් browser menu → **Add to Home screen** භාවිත කරන්න.

### C. Cloud deployment සඳහා API key කියවීම
App එක `.env` file එක local development සඳහා භාවිත කරනවා. Cloud deployment එකේදී Streamlit Secrets ද භාවිත කිරීමට `app.py` හි `generate_ai_report()` function එකේ API key ලබාගන්නා කොටස පහත ලෙස වෙනස් කළ හැකියි:

```python
api_key = os.getenv("OPENAI_API_KEY", "").strip()
if not api_key and hasattr(st, "secrets"):
    try:
        api_key = st.secrets.get("OPENAI_API_KEY", "")
    except Exception:
        api_key = ""
api_key = api_key.strip()
```

එම function එකේ `OPENAI_MODEL` සඳහාත් Streamlit Secrets fallback එකක් අවශ්‍ය නම්:

```python
model = st.text_input(
    "OpenAI model",
    value=os.getenv("OPENAI_MODEL", "gpt-5.5"),
    help="Change only to a model available to your API project."
)
```

Cloud Secrets හි `OPENAI_MODEL` value එක sidebar field එකට default ලෙස ගන්න අවශ්‍ය නම් `st.secrets` fallback එකත් එක් කරන්න.

### D. Phone එකේ දැනගත යුතු දේ
- Internet connection එක අවශ්‍යයි.
- API report generate කරන විට OpenAI API charges ඇති විය හැක.
- App එකට user login / access control තවම නැහැ. URL එක දන්නා අයට app එක open කළ හැකි නිසා sensitive personal data ඇතුළත් නොකරන්න.
- Streamlit Community Cloud availability, usage limits සහ sleep behavior වෙනස් විය හැක.
- Deploy කළ පසු real patient data භාවිත කිරීමට පෙර supervisor approval, privacy/security review සහ clinical review අවශ්‍යයි.
