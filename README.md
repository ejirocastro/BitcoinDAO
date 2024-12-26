# Bitcoin-Based DAO Smart Contract

A decentralized autonomous organization (DAO) smart contract implementation with comprehensive governance, voting, fund management, and investment tracking functionalities.

## Features

- **Governance System**
  - Proposal creation and voting
  - Delegated voting capabilities
  - Configurable voting parameters
  - Timelock period for proposal execution

- **Fund Management**
  - Treasury management
  - Investment return distribution
  - Claim system for returns
  - Emergency controls

- **Security**
  - Emergency admin system
  - Parameter validation
  - Access control
  - Fund safety mechanisms

## Core Parameters

- Proposal Fee: 0.1 STX
- Minimum Proposal Amount: 1 STX
- Maximum Proposal Amount: 1000 STX
- Voting Delay: 100 blocks
- Voting Period: ~1 day (144 blocks)
- Timelock Period: ~12 hours (72 blocks)
- Quorum Threshold: 50%
- Super Majority: 66.7%

## Usage

### Creating a Proposal

```clarity
(contract-call? .dao create-proposal
    "Proposal Title"
    "Proposal Description"
    u1000000  ;; Amount in uSTX
    'SP2ZNGJ85ENDY6QRHQ5P2D4FXKGZWCKTB2T0Z55KF  ;; Target address
)
```

### Delegating Votes

```clarity
(contract-call? .dao delegate-votes
    'SP2ZNGJ85ENDY6QRHQ5P2D4FXKGZWCKTB2T0Z55KF  ;; Delegate address
    u1000000  ;; Amount to delegate
    u144      ;; Expiry block height
)
```

### Claiming Returns

```clarity
(contract-call? .dao claim-returns u1)  ;; Proposal ID
```

## Error Codes

| Code | Description |
|------|-------------|
| u100 | Not authorized |
| u101 | Already voted |
| u102 | Proposal expired |
| u103 | Insufficient funds |
| u104 | Invalid amount |
| u105 | Proposal not active |
| u106 | Quorum not reached |
| u110 | No delegate |
| u111 | Invalid delegate |
| u112 | Emergency active |
| u113 | Not emergency |
| u114 | Invalid parameter |
| u115 | No returns |

## Security Considerations

- Emergency controls are available for critical situations
- Parameter updates require admin authorization
- Fund transfers are protected by multiple validations
- Voting power is tied to contribution amount

## Testing

Comprehensive tests are available covering:
- Proposal creation and voting
- Fund management
- Emergency controls
- Parameter updates
- Return distribution

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## Security

For security concerns, please review our [SECURITY.md](SECURITY.md) file.