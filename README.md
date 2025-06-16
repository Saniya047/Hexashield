## 🔐 HexaShield – Decentralized Storage with Built-in Data Auditing

HexaShield is a secure, user-friendly platform that ensures file integrity across localized fog infrastructures—without requiring full file access or third-party auditors. Inspired by Filecoin, it enables peer-to-peer auditing using lightweight cryptography and probabilistic checks, built for non-technical users and edge environments.

![Dashboard Screenshot](./assets/home.png)

---

## 🚀 Key Highlights

- Cloud Coordination: Stores files, generates cryptographic metadata, and initiates audits.
- Fog Storage & Auditing: Local edge devices store and verify data in a decentralized model.
- No Full File Required: Audits happen securely without full file retrieval.
- Lightweight & Accurate: Uses 4% sampling to detect 1% corruption with 99% accuracy.
- Real-Time Alerts: Instantly detects and reports unauthorized modifications.
- GUI Dashboard: Simple interface for uploads, verification, and results.

---

## 🛠️ Tech Stack

Frontend:
- React.js – Responsive and intuitive UI.

Backend:
- Node.js – API logic and audit handling.
- Socket.IO – Real-time coordination between nodes.
- MongoDB – Metadata and log storage.

Crypto & Verification:
- Algebraic Signatures – Metadata tagging.
- Zero-Knowledge Proofs – Privacy-preserving verification.
- Diffie-Hellman – Security assumptions.
- Ateniese Sampling – Efficient probabilistic integrity checks.

---

## ✨ Features

🔒 Decentralized File Integrity Verification
- Peer-to-peer auditing by fog nodes without needing full file access.

⚡ Real-Time Challenge-Response Auditing
- Homomorphic authenticators and zero-knowledge protocols enable quick audits and tamper alerts.

📊 User-Friendly Dashboard
- React-based interface with visual feedback designed for all users.

---

## 🚀 How to Run on a Local Network

🖥️ System Setup – 3 Machines:
- Cloud PC – Hosts backend and database
- Alice – Auditor
- Bob – Auditee (storage node)

🔁 Step 1: Clone the Repository (All PCs)
git clone https://github.com/Saniya047/HexaShield.git

🌐 Step 2: Backend & Database Configuration
- Ensure all machines are on the same Wi-Fi network.
- On Alice and Bob:
  - Start MongoDB.
  - Start backend using Cloud PC's IP (not localhost).

Replace all 'localhost' references with Cloud IP in:
- .env
- Verification.tsx
- LocalHome.tsx

📁 Step 3: Cloud PC Configuration

Update runScript.js:
- Line 20: Path to SetupTagGen.sh
- Line 21 & 46: Path to 15MBData.csv
- Line 71 & 102: Path to Admin-Cloud folder
- Line 47 & 103: Output destination for Bob.sh
- Line 72: Path to Auditor folder

Update SetupTagGen.sh:
- Replace all instances of 'dataaudit' with your local path.

📁 Step 4: Alice & Bob Configuration

Alice (Auditor):
- Update runScript.js: Line 132 & 194 with your local file path.
- Edit alice.sh:
  - Set path to dataaudit folder.
  - Set Bob's IP address.

Bob (Auditee):
- Update runScript.js: Line 132 & 194 with your local file path.
- Edit bob.sh:
  - Set path to dataaudit folder.
  - Set Alice’s IP address.

🔐 Step 5: Network Permissions (All PCs)
chmod -R +x Demo/
sudo ufw allow 22224
sudo ufw allow 22223

🖥️ Step 6: Start Backend and Frontend (All PCs)
# Terminal 1
cd backend
npm install
npm start

# Terminal 2
cd frontend
npm install
npm run dev

✅ Step 7: Workflow Execution

1. Register Users:
   - Cloud PC: Register as `cloud`
   - Alice & Bob: Register as `local`

2. Cloud PC:
   - Upload a file and generate metadata.
   - Send file to Bob.
   - Share verification data with Alice and Bob.
   - Click “Send Verification.”

3. Bob PC:
   - Run bob.sh to initiate communication.

4. Alice PC:
   - Run alice.sh to perform the audit.
   - Result auto-sent to cloud and visible on the dashboard.

---

✅ You’re All Set!
HexaShield is now live on your local network—delivering real-time decentralized file integrity verification with ease.

📌 Questions? Open an issue on the GitHub repository.
