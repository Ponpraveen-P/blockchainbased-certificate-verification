# blockchainbased-certificate-verification
CertChain — Blockchain-Based Certificate Verification System
A full-stack final-year college project that lets institutions issue tamper-proof
digital certificates. Every certificate's SHA-256 hash is stored on the Ethereum
blockchain via a Solidity smart contract, so anyone can verify its authenticity
instantly by Certificate ID or QR code — independent of the institution's database.
Tech Stack
React.js · Node.js/Express · MySQL · Solidity · Ganache · Web3.js · JWT · bcrypt
Project Structure
```
certchain/
├── backend/     Express REST API, smart contract, PDF/QR/hash utilities
├── frontend/    React SPA (admin, student, and public verification portals)
├── database/    MySQL schema + sample data
├── docs/        Folder structure & documentation
└── report/      College project report (see docs/)
```
Quick Start
1. Database
```bash
mysql -u root -p < database/certchain_schema.sql
```
2. Blockchain (Ganache)
Install & open Ganache → creates a local chain on `http://127.0.0.1:7545`
Copy one account's address + private key from Ganache
3. Backend
```bash
cd backend
npm install
cp .env.example .env      # then fill in DB + Ganache account details
npm run deploy-contract   # deploys the smart contract, prints CONTRACT_ADDRESS
# paste the printed address into .env as CONTRACT_ADDRESS
npm run seed-admin        # creates default admin login (admin@certchain.edu / Admin@123)
npm run dev                # starts API on http://localhost:5000
```
4. Frontend
```bash
cd frontend
npm install
cp .env.example .env
npm start                  # starts React app on http://localhost:3000
```
5. Try it
Admin login: `admin@certchain.edu` / `Admin@123` (change after first login)
Issue a certificate from the Admin Dashboard → it hashes, stores on-chain, generates PDF + QR
Visit `/verify` and enter the Certificate ID (or scan the QR) to verify it publicly
Full Documentation
See `docs/01_FOLDER_STRUCTURE.md` for the complete file-by-file breakdown.
License
Built for academic/educational submission. Free to reuse and extend.
