# Stacks-SkySyncProtocol - Weather Data Oracle Smart Contract

## Overview
The Weather Data Oracle is a decentralized smart contract that enables IoT devices to submit weather data, validates submissions through consensus, and rewards accurate contributions. It ensures data integrity through staking mechanisms, penalties for inaccurate reporting, and governance-based parameter adjustments.

## Features
- **Device Registration**: Devices must be registered with unique IDs and associated with their owners.
- **Staking Mechanism**: Device owners must stake tokens to participate and receive rewards.
- **Weather Data Submission**: Devices submit temperature, humidity, pressure, and wind speed readings.
- **Consensus Validation**: Data is validated against consensus to ensure accuracy.
- **Reward Distribution**: Devices submitting accurate data are rewarded in STX tokens.
- **Penalties for Inaccuracy**: Devices submitting inaccurate data receive penalties.
- **Governance System**: Stakeholders can propose and vote on contract parameters.

## Smart Contract Components

### Constants
- `min-stake`: Minimum amount required to stake a device.
- `reward-per-submission`: Reward per validated data submission.
- `max-deviation`: Maximum allowed deviation for consensus validation.
- `min-validators`: Minimum validators required for consensus.
- `accuracy-threshold`: Minimum accuracy score required for participation.
- `penalty-amount`: Penalty for low accuracy submissions.
- `max-inactive-blocks`: Maximum blocks allowed before marking a device inactive.
- `governance-threshold`: Minimum votes required to pass a proposal.

### Error Codes
- `ERR-NOT-AUTHORIZED`: Unauthorized access attempt.
- `ERR-DEVICE-EXISTS`: Device is already registered.
- `ERR-INVALID-STAKE`: Insufficient stake amount.
- `ERR-DEVICE-NOT-FOUND`: Device does not exist.
- `ERR-INVALID-DATA`: Submitted data is invalid.
- `ERR-CONSENSUS-FAILED`: Data validation failed.
- `ERR-LOW-ACCURACY`: Device accuracy is below threshold.
- `ERR-INACTIVE-DEVICE`: Device has been inactive for too long.
- `ERR-INSUFFICIENT-STAKE`: Insufficient stake to propose governance changes.
- `ERR-INVALID-PROPOSAL`: Proposal parameters are invalid.

### Data Structures
- **Devices**: Stores registered devices, their owners, stake amounts, accuracy scores, and locations.
- **Weather Data**: Stores submitted weather data, timestamps, and validation status.
- **Consensus Data**: Aggregated data used for validation.
- **Device Metrics**: Tracks last submission block, consecutive validations, total rewards, and penalties.
- **Proposals**: Stores governance proposals and voting results.
- **Votes Cast**: Stores votes from participants on governance proposals.

## Functions

### Public Functions
1. **register-device(device-id, latitude, longitude)**: Registers a new IoT device.
2. **stake-device(device-id, amount)**: Stakes tokens for a device.
3. **submit-data(device-id, timestamp, temperature, humidity, pressure, wind-speed)**: Submits weather data for validation.
4. **validate-data(device-id, timestamp, location-hash)**: Validates submitted weather data based on consensus.
5. **report-malfunction(device-id)**: Reports a malfunctioning device for penalties.
6. **update-device-status(device-id)**: Checks device activity and updates accuracy score.
7. **create-proposal(title, description, parameter, new-value)**: Proposes a governance change.
8. **vote-on-proposal(proposal-id, vote-value)**: Votes on a governance proposal.

### Read-Only Functions
1. **get-device-info(device-id)**: Retrieves information about a device.
2. **get-weather-data(device-id, timestamp)**: Retrieves weather data submitted by a device.
3. **get-consensus-data(location-hash, timestamp)**: Retrieves consensus-based weather data.
4. **get-device-by-owner(owner)**: Finds a device registered to an owner.

## Governance
The contract supports decentralized governance where stakeholders can propose and vote on contract parameter changes. Proposals must be backed by a minimum stake and reach a majority threshold to be enacted.

## Security & Validation
- Uses stake-based incentives and penalties to ensure data integrity.
- Consensus-based validation to prevent false data submissions.
- Governance mechanisms to adjust contract parameters dynamically.
