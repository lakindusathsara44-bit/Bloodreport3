# Project notes

## Architecture
- `app.py`: Streamlit interface, data validation, charts, OpenAI Responses API call, PDF generation.
- `.env`: local secret configuration (create from `.env.example`; not included in ZIP).
- `requirements.txt`: Python dependencies.
- `README_SI.md`: Sinhala Windows setup guide.

## Academic and clinical safety boundaries
This is a student educational prototype, not a certified medical device or clinically validated decision-support system. The application does not diagnose, prescribe, or calculate a diagnosis from threshold rules. The AI receives entered values only when the user explicitly requests report generation. For real deployments, consult the project supervisor and qualified clinical, privacy, and security professionals.

## Before final submission
- Ask the supervisor to approve the implementation scope and report template.
- Add screenshots, test cases, test results, limitations, and diagrams to the HNDIT1052 final report.
- Use synthetic test values in demonstrations.
- Do not claim clinical validation.
