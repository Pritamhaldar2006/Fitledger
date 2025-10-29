
# 🏋️‍♂️ FitLedger

### Your Immutable Fitness Journal on the Blockchain

---

## 📖 Project Description

**FitLedger** is a simple beginner-friendly Solidity smart contract that allows users to **store their daily fitness logs immutably** on the blockchain.  
Each user’s workout records are securely tied to their wallet address — ensuring privacy, transparency, and permanence.  

Perfect for anyone learning how to build decentralized applications (dApps) and exploring how blockchain can be used for **personal data tracking**.
<img width="1920" height="1020" alt="smartContract" src="https://github.com/user-attachments/assets/4e306374-a74f-46f3-b04c-1f0741911c63" />


---

## ⚙️ What It Does

FitLedger lets users:

1. **Record daily fitness activities** such as running, cycling, yoga, or gym workouts.  
2. **Store them permanently** on the Ethereum blockchain — no one can alter or delete them.  
3. **Retrieve their fitness history** anytime from their wallet.  
4. Emit blockchain events every time a new workout is added.

---

## ✨ Features

- 🧍 User-specific fitness log storage  
- 🕒 Immutable record of workouts  
- 📅 Stores date, activity, duration, and notes  
- 📜 View all your personal logs  
- ⚡ Emits `LogAdded` event for every new entry  
- 🔒 Fully decentralized and secure  

---

## 🔗 Deployed Smart Contract

Deployed on: **XXX**  
*(Replace this with your deployed smart contract address or testnet link once deployed)*

---

## 💻 Smart Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract FitLedger {
    // Structure to store a fitness log
    struct FitnessLog {
        string date;          // e.g. "2025-10-29"
        string activity;      // e.g. "Running"
        uint256 duration;     // in minutes
        string notes;         // optional notes or comments
    }

    // Mapping user address to their list of logs
    mapping(address => FitnessLog[]) private userLogs;

    // Event for tracking new log entries on the blockchain
    event LogAdded(address indexed user, string date, string activity, uint256 duration);

    // Function to add a new fitness log
    function addLog(
        string memory _date,
        string memory _activity,
        uint256 _duration,
        string memory _notes
    ) public {
        FitnessLog memory newLog = FitnessLog({
            date: _date,
            activity: _activity,
            duration: _duration,
            notes: _notes
        });

        userLogs[msg.sender].push(newLog);

        emit LogAdded(msg.sender, _date, _activity, _duration);
    }

    // Function to get all logs of the user who calls it
    function getMyLogs() public view returns (FitnessLog[] memory) {
        return userLogs[msg.sender];
    }
}
