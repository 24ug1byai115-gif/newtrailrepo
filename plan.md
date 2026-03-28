MailMind — Complete Plan Start Se

Abhi Karo — 5 min
Terminal kholo aur ek ek chalao:
pip install fastapi uvicorn
pip install google-generativeai
pip install scikit-learn nltk
pip install vaderSentiment
pip install chromadb
pip install google-api-python-client
pip install google-auth-oauthlib
pip install python-dotenv pandas numpy

Step 1 — Folder Structure Banao — 5 min
Desktop pe yeh banao manually:
MailMind/
├── backend/
│   ├── main.py
│   ├── gmail_agent.py
│   ├── spam_detector.py
│   ├── sentiment.py
│   ├── intent_classifier.py
│   ├── confidence.py
│   ├── reply_generator.py
│   └── .env
├── frontend/
└── models/

Step 2 — Gemini API Key Lao — 10 min

aistudio.google.com pe jao
Google account se login karo
Get API Key click karo
Copy karo key

.env file mein likho:
GEMINI_API_KEY=paste_here

Step 3 — Gmail API Setup — 30 min

console.cloud.google.com pe jao
New Project — naam MailMind
APIs and Services → Enable APIs
Gmail API enable karo
Google Calendar API enable karo
Credentials → Create → OAuth Client ID → Desktop App
JSON download karo
Rename karo credentials.json
MailMind/backend/ mein rakho


Step 4 — Dataset Download karo — 15 min

kaggle.com pe jao
Search — Enron Email Spam Dataset
Download emails.csv
MailMind/models/ mein rakho


Step 5 — Copilot Se Files Generate karo — 2 hrs
VS Code mein Copilot open karo
Yeh order follow karo —

File 1 — spam_detector.py
Write Python code to train spam detector using
TF-IDF and Naive Bayes on Enron dataset at
models/emails.csv. Save model as
models/spam_model.pkl. Write predict function
that takes email text and returns is_spam
and confidence score percentage.

File 2 — sentiment.py
Write Python function using VADER sentiment
analysis. Input is email text. Output is
positive, negative or neutral label and
compound score. No API needed.

File 3 — intent_classifier.py
Write Python code to classify email intent
using Logistic Regression. 7 intents are
meeting_request, complaint, inquiry,
follow_up, feedback, urgent, general.
Save model as models/intent_model.pkl.
Predict function returns intent and
confidence percentage.

File 4 — confidence.py
Write Python function that takes confidence
score as input. If above 85 return auto_send.
If between 60 and 85 return flag_review.
If below 60 return escalate_human.

File 5 — memory.py
Write Python code using ChromaDB to store
email and its reply as memory. Write retrieve
function that takes new email text and returns
top 3 similar past emails with their replies.

File 6 — reply_generator.py
Write Python function using Google Gemini API
with model gemini-1.5-flash. Load API key
from .env file. Take email text, sender name,
sentiment label, intent label and past context
as input. Generate professional email reply.
Return reply text.

File 7 — gmail_agent.py
Write Python code using Gmail API to connect
using credentials.json with OAuth 2.0. Write
fetch function to get unread emails and return
list with id, sender, subject, body. Write
send function that takes email id and reply
text and sends the reply. Save token as
token.json after first login.

File 8 — main.py
Write FastAPI app that combines all these
files. One endpoint /process-emails that
fetches emails from Gmail, checks spam,
analyzes sentiment, classifies intent,
checks confidence score, generates Gemini
reply, and auto sends if confidence above 85.
Add CORS middleware. Add /analytics endpoint
returning processed count, spam count,
auto replied count.

Step 6 — Train Models — 30 min
Terminal mein chalao:
cd MailMind/backend
python spam_detector.py
python intent_classifier.py
Dono .pkl files models/ folder mein ban jayengi

Step 7 — Backend Test karo — 20 min
cd MailMind/backend
uvicorn main:app --reload
Browser mein kholo:
localhost:8000/docs
/process-emails click karo — pehli baar Gmail login popup aayega — allow karo

Step 8 — Frontend Banao — 1.5 hrs
Terminal mein:
cd MailMind
npx create-react-app frontend
cd frontend
npm install axios recharts
Copilot se generate karo:
Dashboard.jsx:
Write React component with Tailwind CSS for
email dashboard showing 4 stat cards:
Emails Processed, Auto Replied, Spam Blocked,
Meetings Booked. Fetch data from
localhost:8000/analytics every 5 seconds.
Dark theme with blue accent colors.
EmailList.jsx:
Write React component showing list of
processed emails with sender, subject,
intent badge, sentiment badge, action taken
and generated reply. Fetch from
localhost:8000/process-emails.

Step 9 — Connect Frontend to Backend — 15 min
App.jsx mein:
Import Dashboard and EmailList components
Show Dashboard at top
Show EmailList below
Clean dark background
Chalao:
npm start

Step 10 — End to End Test — 30 min

Apni email se apne aap ko ek email bhejo
Backend chalao
Dekho kya result aaya
Dashboard mein numbers update hue kya
Reply gaya kya


Total Time
StepTimeInstall + Setup1 hrGemini + Gmail API45 minDataset download15 minCopilot se files2 hrsModel training30 minBackend test20 minFrontend1.5 hrsFinal test30 minTotal~7 hrs

Sabse Pehle Karo Abhi

pip install wale commands chalao
Folder structure banao
Gemini API key lao
Gmail API setup karo

Yeh charo ho gaye toh baki sab fast hoga
Kahan se shuru kar rahe ho — bolo!