# Student Eligibility Pass

A privacy-preserving student eligibility dApp built on the [Midnight Network](https://midnight.network/).

Student Eligibility Pass allows a student to prove that they satisfy academic eligibility requirements without revealing their exact CGPA or attendance.

The project demonstrates how Midnight's privacy model, Compact smart contracts, private state, witnesses, and zero-knowledge proofs can be used to protect sensitive academic information while still providing verifiable eligibility results.

---

## 🎯 Project Overview

Educational institutions may need to verify whether a student satisfies requirements such as:

- Minimum CGPA
- Minimum attendance

Traditional verification requires the student to disclose their actual academic values.

**Student Eligibility Pass changes this by allowing the student to prove eligibility without revealing the underlying CGPA or attendance values.**

### Eligibility Requirements

| Requirement | Threshold |
|---|---:|
| CGPA | ≥ 8.00 |
| Attendance | ≥ 75% |

The student's actual academic values are maintained in private state and accessed by the Compact contract through witness functions.

---

## ✨ Features

- 🔐 Privacy-preserving eligibility verification
- 🎓 Student eligibility credential
- 🧾 Credential issuance
- ✅ Zero-knowledge eligibility proof
- 🔄 Credential revocation
- 📊 Public credential status
- 🔢 Credential version tracking
- 👛 Midnight wallet integration
- 🌐 Midnight Preprod network support
- ⚡ React + TypeScript frontend
- 🧩 Compact smart contract
- 🔑 Generated proving and verifying keys
- 📋 Contract address display and copy functionality

---

# 🔒 Privacy Model

Privacy is the central purpose of Student Eligibility Pass.

## Private Information

The following information is maintained as private state:

- Student CGPA
- Student attendance
- Student secret key

The frontend does not need to publish the student's exact CGPA or attendance to the blockchain.

The private values are supplied to the Compact circuit through witnesses during proof generation.

## What a Blockchain Observer Can Learn

An observer can see publicly observable information such as:

- Contract address
- Public contract state
- Credential status
- Credential version
- Public transaction information
- The public outcome/state associated with a submitted proof

## What an Observer Cannot Learn

The privacy-preserving proof does not expose the student's exact:

- CGPA
- Attendance

For example, the student can prove:

```text
CGPA ≥ 8.00
Attendance ≥ 75%
without publishing values such as:

CGPA = 8.50
Attendance = 85%

The purpose of the zero-knowledge proof is to demonstrate that the required conditions are satisfied without revealing the underlying private values.

🧪 How the Privacy Proof Works

The application follows this flow:

Student
   │
   │ Private CGPA + Attendance
   ▼
Private State
   │
   │ Witness Functions
   ▼
Compact Smart Contract
   │
   │ Eligibility Circuit
   ▼
Zero-Knowledge Proof
   │
   ▼
Midnight Network
   │
   ├── Public Credential Status
   ├── Credential Version
   └── Public Transaction State
Step-by-step
The student's academic information is stored in private state.
Witness functions provide the private values to the Compact circuit.
The eligibility circuit evaluates the required conditions.
Midnight generates a zero-knowledge proof.
The blockchain records the appropriate public state and transaction information.
The exact CGPA and attendance values remain private.
🏗️ Architecture
                    Student
                       │
                       ▼
              Midnight Wallet
                       │
                       ▼
             React + TypeScript UI
                       │
                       ▼
                Midnight.js API
                       │
                       ▼
              Compact Smart Contract
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
       Issue        Prove        Revoke
     Credential   Eligibility   Credential
                       │
                       ▼
              Zero-Knowledge Proof
                       │
                       ▼
                Midnight Preprod
Project Structure
student-eligibility-pass-level3/
│
├── contract/
│   └── src/
│       ├── bboard.compact
│       ├── index.ts
│       ├── witnesses.ts
│       └── managed/
│           └── bboard/
│
├── api/
│   └── src/
│       ├── index.ts
│       └── common-types.ts
│
├── bboard-ui/
│   ├── src/
│   │   ├── App.tsx
│   │   ├── components/
│   │   ├── contexts/
│   │   └── hooks/
│   └── public/
│
└── bboard-cli/
🔐 Smart Contract

The Compact smart contract provides three primary operations.

Issue Eligibility Credential

Creates or activates an eligibility credential for the student.

The application updates the public credential state while keeping the student's academic information private.

Prove Eligibility

The student submits an eligibility proof.

The private CGPA and attendance are used by the circuit to verify the required conditions.

A successful proof demonstrates eligibility without exposing the exact academic values.

Revoke Credential

The active credential can be revoked.

The public credential state is updated to reflect the revocation.

🖥️ Frontend

The React frontend provides a simple interface for interacting with the privacy-preserving credential.

Available functionality
Create Eligibility Pass
Issue Eligibility Credential
View credential status
View credential version
Prove Eligibility
Revoke Credential
View contract address
Copy contract address
Display transaction success/error messages
Successful Verification

The completed frontend flow has been tested successfully.

The application displayed:

Credential Active


Credential version: 3


Eligibility verified ✓


Eligibility proven successfully without revealing CGPA or attendance.
👛 Wallet Integration

The application uses the Midnight wallet for blockchain interaction.

The wallet is used to:

Connect the student to the dApp
Authorize transactions
Interact with the deployed contract
Submit privacy-preserving transactions
Wallet Evidence

The final submission will include a screenshot showing the connected Midnight wallet and network configuration.

Screenshot:

docs/screenshots/wallet.png
📜 Contract Deployment

The Student Eligibility Pass contract has been tested on the Midnight Preprod network.

Contract Address
TODO: ADD DEPLOYED CONTRACT ADDRESS
Contract Address Screenshot

The final submission will include evidence showing the deployed contract address.

docs/screenshots/contract-address.png
🌐 Network

The application has been tested using the:

Midnight Preprod Network

The frontend connects through the Midnight wallet and uses the local proof server for zero-knowledge proof generation.

🚀 Running the Project
Prerequisites

Make sure the following are installed:

Node.js 24+
npm
Docker Desktop
Compact compiler
Midnight wallet

Check Node.js:

node --version

Check npm:

npm --version

Check Docker:

docker --version
Install Dependencies

From the project root:

npm install
Compile the Compact Contract
cd contract
npm run compact
npm run build
cd ..
Build the API
cd api
npm run build
cd ..
Build the Frontend
cd bboard-ui
npm run build

The frontend build also copies the generated proving/verifying keys and ZKIR files required by the application.

Start the Frontend

After building:

npm run start

The exact command may depend on the local environment and selected Midnight network.

🧪 Testing

Automated tests are part of the Level 3 submission requirements.

Test Requirement

The project must demonstrate:

Minimum 3 tests passing
Test Command
cd contract
npm test
Test Evidence

A screenshot showing the successful test output will be added here:

docs/screenshots/tests.png
Test Result
TODO: ADD FINAL TEST OUTPUT
⚙️ CI/CD

The project submission requires a CI/CD workflow with a passing run.

The repository will include a GitHub Actions workflow for automated validation.

The workflow will verify items such as:

TypeScript compilation
Contract compilation
Tests
Linting
Build validation
CI/CD Evidence

GitHub Actions workflow:

TODO: ADD WORKFLOW LINK / BADGE

Passing workflow screenshot:

docs/screenshots/ci-passing.png
📸 Demo Evidence

The final submission will include screenshots demonstrating the complete working flow.

Screenshot 1 — Midnight Wallet
docs/screenshots/wallet.png

Shows:

Connected wallet
Midnight network
Wallet balance/network configuration
Screenshot 2 — Contract Address
docs/screenshots/contract-address.png

Shows:

Deployed contract address
Screenshot 3 — Credential Issued
docs/screenshots/credential-issued.png

Shows:

Successful credential issuance
Screenshot 4 — Credential Active
docs/screenshots/credential-active.png

Shows:

Credential Active
Credential version
Screenshot 5 — Eligibility Verified
docs/screenshots/eligibility-verified.png

Shows:

Eligibility verified ✓

and:

Eligibility proven successfully without revealing CGPA or attendance.
Screenshot 6 — Frontend
docs/screenshots/frontend.png

Shows the complete Student Eligibility Pass interface.

🎥 Demo Video

A short demonstration video will show the complete application flow.

The target duration is approximately:

1 minute

Demo Flow
1. Connect Midnight wallet
        ↓
2. Create Eligibility Pass
        ↓
3. Issue Eligibility Credential
        ↓
4. Show Credential Active
        ↓
5. Prove Eligibility
        ↓
6. Show Eligibility Verified
Demo Video
TODO: ADD DEMO VIDEO LINK
🔗 Links
GitHub Repository

https://github.com/KrushnaSPPUDoT-code/student-eligibility-pass-level3

Live Demo
TODO: ADD LIVE DEMO URL
Deployed Contract
TODO: ADD CONTRACT ADDRESS
Demo Video
TODO: ADD VIDEO LINK
📋 Level 3 Submission Checklist
Requirement	Status
Functional Midnight dApp	✅
Meaningful use of Midnight privacy model	✅
Minimum 3 tests passing	⏳
CI/CD workflow	⏳
Passing CI/CD run	⏳
Approved idea	⏳
Public GitHub repository	✅
Complete README	🔄
Live demo	⏳
Test-output screenshot	⏳
CI/CD evidence	⏳
One-minute demo video	⏳
Privacy model section	✅
Product proposal approval evidence	⏳
Minimum 10 meaningful commits	⏳
📊 Current Development Status

The current Level 3 implementation successfully demonstrates:

Midnight wallet connection
Contract deployment
Eligibility credential issuance
Active credential state
Credential version tracking
Eligibility proof
Successful privacy-preserving verification
Contract address display
Contract address copy functionality
React frontend integration
Midnight.js API integration
Private student CGPA and attendance state
Witness-based access to private values
Zero-knowledge eligibility verification

The successful frontend verification demonstrated that the student can prove eligibility without displaying their exact CGPA or attendance.

🧑‍💻 Technology Stack
Technology	Purpose
Midnight Network	Privacy-preserving blockchain
Compact	Smart contract language
Midnight.js	Contract and wallet integration
React	Frontend
TypeScript	Application development
Vite	Frontend build tooling
Material UI	User interface
Docker	Local proof server
Zero-Knowledge Proofs	Private eligibility verification
GitHub Actions	CI/CD
🔒 Security and Privacy Principles

Student Eligibility Pass follows a privacy-first design.

Sensitive academic information is not intentionally exposed through the public UI or public contract state.

The application's core privacy principle is:

Prove the condition, not the underlying data.

Instead of publishing:

CGPA = 8.50
Attendance = 85%

the application allows the student to demonstrate:

CGPA ≥ 8.00
Attendance ≥ 75%

while keeping the underlying values private.

📄 License

This project is developed as part of the Midnight Level 3 project.

Built with:

Midnight Network
Compact
Midnight.js
React
TypeScript
🙌 Student Eligibility Pass

A privacy-preserving way to prove academic eligibility without exposing private academic data.



### After pasting


In nano:


**Save:**
```text
Ctrl + O
Enter

Exit:

Ctrl + X

Then run:

wc -l README.md
git diff --check
git status

If git diff --check gives no output, that's good.
