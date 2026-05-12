# VIN Automation — Setup Checklist

Use this as the build gate before going live. All items must be checked before the first real run.

## POWER PLATFORM

- [ ] Correct environment selected in Power Automate
- [ ] User has **Environment Maker** role in that environment
- [ ] Required Power Automate license confirmed (Microsoft 365 seeded or standalone)
- [ ] Cloud flow created inside a **Solution** (not My Flows)
- [ ] SharePoint connection created and tested
- [ ] Desktop flows connection created and points to registered PAD machine
- [ ] Flow owner assigned; backup co-owner added
- [ ] Run-only users configured for Power App end users

## SHAREPOINT

- [ ] `VIN_Check_Requests` list created (schema: sharepoint/VIN_Check_Requests.schema.json)
- [ ] `VIN_Check_Results` list created (schema: sharepoint/VIN_Check_Results.schema.json)
- [ ] `VIN_Audit_Log` list created (schema: sharepoint/VIN_Audit_Log.schema.json)
- [ ] `Vehicle_Appraisals` list created or confirmed existing (schema: sharepoint/Vehicle_Appraisals.schema.json)
- [ ] `VINEvidence` document library created for screenshots
- [ ] Flow service account has **Contribute** access to all four lists and evidence library
- [ ] End users do NOT have direct edit access to `VIN_Audit_Log`

## PAD MACHINE

- [ ] Windows Pro / Enterprise / Server machine (not Home edition)
- [ ] Latest Power Automate Desktop installed via IT-approved MSI
- [ ] Machine-runtime app option selected during install
- [ ] Machine signed in and registered to the correct Power Platform environment
- [ ] Machine name set to `QASIM-COE-VIN-PAD-01` (or your chosen name in parameters.json)
- [ ] User has **Environment Maker** or **Desktop Flow Machine Owner** role
- [ ] Browser extension enabled for Edge and/or Chrome
- [ ] Dedicated Edge profile created for VIN automation work
- [ ] Power Platform network endpoints reachable (test with PAD diagnostic tool):
  - `*.dynamics.com`
  - `*.servicebus.windows.net`
  - `*.gateway.prod.island.powerapps.com`
  - `*.api.powerplatform.com`

## BROWSER / PORTALS (manual pre-flight)

- [ ] Google accessible and returns results for a test VIN
- [ ] MOI UAE Accidents Inquiry page loads correctly
- [ ] Autorola Fleet Monitor loads and user can sign in manually
- [ ] No CAPTCHA bypass configured or attempted
- [ ] No credentials stored in PAD flow variables

## PARAMETERS

- [ ] `config/parameters.json` filled in with real environment/site values
- [ ] `PADFlowId` updated after registering the PAD flow
- [ ] `PADConnectionName` updated after creating the desktop flows connection

## GOVERNANCE

- [ ] Evidence screenshot path configured and folder exists
- [ ] RunId generated per check (handled automatically by cloud flow)
- [ ] Audit log entry written for every source (Google, MOI, Autorola, System)
- [ ] Exact VIN match enforced before Autorola comment write
- [ ] Duplicate VIN → ManualReview disposition confirmed in test
- [ ] Accident / salvage flag → TradeOnly disposition confirmed in test
- [ ] Manual review gate displays correctly in Power App

## SIGN-OFF

- [ ] Test run completed with a known VIN (non-production data)
- [ ] Audit log entries verified in SharePoint
- [ ] Evidence screenshots visible in VINEvidence library
- [ ] Authorised by: _______________
- [ ] Date: _______________
