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

