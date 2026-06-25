# Windows Server RDS Learning Path 59 — Troubleshoot RDS Licensing Warnings

**Level:** Expert · **Module:** 59/70

## Goal
Diagnose licensing-mode, discovery, activation, version and CAL availability warnings without bypassing licensing.

## Workflow
1. Capture the exact Licensing Diagnoser warning and current evaluation/grace state.
2. Verify the deployment's licensing mode and server list.
3. Check license-server service and activation state.
4. Confirm Session Host, license server and CAL versions are compatible.
5. Review available and issued CAL reports.
6. Review TerminalServices-Licensing events.
7. Correct configuration or entitlement and retest an approved connection.

```powershell
Get-RDLicenseConfiguration -ConnectionBroker 'RDS01.corp.lab'
Get-Service TermServLicensing
Get-WinEvent -LogName 'Microsoft-Windows-TerminalServices-Licensing/Operational' `
 -MaxEvents 100 -ErrorAction SilentlyContinue
```

## Evidence
Store Diagnoser output, mode/server settings, version matrix, CAL report, events, root cause and post-fix connection under `evidence/`.

## Troubleshooting
Common causes are wrong mode, undiscovered server, stopped service, version incompatibility or insufficient legitimate entitlements.

## Security and compliance
Do not reset grace periods or delete licensing state. Correct the configuration and licensing position.

## Rollback
Restore only the recorded licensing configuration through Deployment Properties/GPO.

## Next
`Windows-Server-RDS-Learning-Path-60-Troubleshoot-RDS-Profile-Problems`
