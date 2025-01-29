# Vaccine Tracking Smart Contract

## Overview
This smart contract implements a comprehensive vaccine tracking and immunization management system on the blockchain. It handles vaccine shipment logistics, cold chain monitoring, immunization records, and clinical authorization management.

## Features
- Vaccine shipment registration and tracking
- Cold chain temperature monitoring
- Immunization record management
- Clinical staff authorization
- Storage facility management
- Comprehensive data validation

## Core Components

### Data Structures

#### Vaccine Shipment Registry
Tracks vaccine shipments with details including:
- Manufacturer information
- Brand name
- Production and expiration dates
- Available doses
- Storage temperature
- Shipment status
- Temperature violation incidents
- Storage facility location
- Additional notes

#### Immunization Registry
Manages recipient immunization records including:
- Immunization sequence (up to 10 entries)
- Completed immunization count
- Adverse event reports
- Medical exemptions

#### Authorized Clinicians
Maintains clinician credentials:
- Clinical role
- Clinic affiliation
- Credential expiration date

#### Cold Chain Facilities
Tracks storage facility information:
- Location details
- Storage capacity
- Current inventory
- Temperature monitoring history

### Key Functions

#### Administrative Functions
- `transfer-system-control`: Transfer system controller privileges
- `register-clinician`: Add new authorized clinicians
- `register-storage-facility`: Register new storage facilities

#### Vaccine Management
- `register-vaccine-shipment`: Record new vaccine shipments
- `update-shipment-status`: Update shipment status
- `record-temperature-violation`: Log temperature violations

#### Immunization Management
- `record-immunization`: Record vaccine administration
- `verify-vaccine-validity`: Check vaccine status and validity

#### Read-Only Functions
- `get-shipment-details`: Retrieve shipment information
- `get-recipient-record`: Access recipient immunization records
- `get-facility-details`: View facility information
- `verify-clinician-status`: Check clinician authorization

## Constants and Limitations
- Cold Chain Temperature Range: -70°C to 8°C
- Minimum Dose Interval: 21 days
- Maximum Immunization Series: 4 doses
- Temperature Violation Threshold: 2 incidents

## Error Codes
- `u100`: Authorization Error
- `u101`: Invalid Vaccine Shipment
- `u102`: Duplicate Shipment
- `u103`: Shipment Not Found
- `u104`: Vaccine Supply Depleted
- `u105`: Invalid Recipient ID
- `u106`: Duplicate Immunization
- `u107`: Cold Chain Breach
- `u108`: Expired Vaccine
- `u109`: Invalid Clinic Location
- `u110`: Immunization Limit Reached
- `u111`: Minimum Interval Violation
- `u112`: Admin Privileges Required
- `u113`: Data Validation Error
- `u114`: Expiry Date Error
- `u115`: Storage Capacity Error

## Security Features
- System controller authentication
- Clinician authorization verification
- Data validation for all inputs
- Temperature monitoring and alerts
- Expiration date tracking
- Dose interval enforcement

## Data Validation
The contract implements comprehensive validation for:
- String inputs (minimum length requirements)
- Date fields (future date validation)
- Storage limits
- Temperature ranges
- Authorization status
- Immunization intervals

## Usage Examples

### Registering a New Vaccine Shipment
```clarity
(contract-call? .vaccine-tracking register-vaccine-shipment
    "SHIP123" 
    "Manufacturer-Name"
    "Vaccine-Brand"
    u1643673600 
    u1659225600
    u1000
    2
    "FACILITY001")
```

### Recording an Immunization
```clarity
(contract-call? .vaccine-tracking record-immunization
    "PATIENT123"
    "SHIP123"
    "Clinic-Location-A")
```

## Best Practices
1. Always verify clinician authorization before performing operations
2. Monitor cold chain temperatures regularly
3. Update shipment status promptly
4. Validate recipient records before immunization
5. Maintain accurate facility records

## Note
This smart contract is designed for production use with emphasis on:
- Data integrity
- Security
- Regulatory compliance
- Efficient record keeping
- Temperature control monitoring