
# Operation Rotor Trace
## Aviation Forensics Investigation - The Helicopter Crash

---

## Case Overview

In this project, I conducted a full digital forensic examination of a fictional aviation accident involving a Bell 412 helicopter (Registration: XAL-412) operated by Xavier Air Logistics.

The objective of this investigation was not simply to determine why the aircraft crashed, but to establish whether digital evidence indicated:

- Maintenance negligence
- Record manipulation
- Component irregularities
- Evidence concealment
- Mechanical failure
- Human decision-making failures
- Operational pressure prior to flight

Using forensic artefacts recovered from a maintenance workstation, USB storage device, mobile communications, aircraft telemetry, Flight Data Recorder (FDR), Cockpit Voice Recorder (CVR), HUMS records, ATC communications and weather data, I reconstructed the sequence of events leading to the loss of the aircraft.

The investigation ultimately revealed evidence of maintenance record modification, serial number inconsistencies, attempted concealment activity, known gearbox-related concerns before departure, and a progressive in-flight mechanical failure that culminated in the crash.

---

## Disclaimer

This repository documents a forensic investigation performed on a **fictional training scenario** created for educational and professional development purposes.

All organisations, aircraft registrations, personnel names, communications, maintenance records, and evidentiary artefacts referenced throughout this repository are part of the training dataset supplied for the exercise.

This repository does not contain evidence from any real-world aviation accident.

The findings, conclusions, timelines and analysis presented here were developed solely from the supplied training artefacts and are intended to demonstrate forensic methodology, evidence correlation, timeline reconstruction, and digital investigation techniques.

---

# Investigation Objectives

During this examination I sought to answer the following questions:

1. What was the original maintenance status of the helicopter?
2. Was the maintenance status altered?
3. Who performed the alteration?
4. When was the alteration made?
5. Was an unapproved component installed?
6. Do component records support the installed hardware?
7. Were there attempts to conceal evidence?
8. What communications occurred before the flight?
9. What happened during the final flight?
10. Did the route deviation contribute to the crash?
11. What was the most probable sequence of events leading to the accident?

---

# Evidence Examined

The investigation involved multiple evidence sources.

| Evidence Source | Description |
|----------------|-------------|
| Maintenance Laptop Image | The Crashed Helicopter.img |
| USB Storage Device | Kingston DataTraveler 3.0 |
| Maintenance Audit Logs | Component and release records |
| Maintenance Status Reports | Original and modified versions |
| Component Certificates | Supplier and certification documents |
| Browser History | Chrome activity on maintenance workstation |
| Deleted Files | Recovered maintenance records |
| Mobile Communications | Messages between flight and maintenance personnel |
| Flight Data Recorder | Aircraft operational data |
| HUMS Data | Health and Usage Monitoring System |
| Flight Telemetry | Aircraft movement and performance data |
| CVR Transcript | Cockpit Voice Recorder |
| ATC Logs | Air Traffic Control communications |
| Weather Reports | Flight weather information |
| GPS Route Data | Planned and actual route information |

---

# Forensic Methodology

My investigation followed standard digital forensic procedures:

1. Evidence Verification
2. Evidence Preservation
3. Hash Validation
4. Evidence Ingestion
5. Artifact Extraction
6. Timeline Reconstruction
7. Correlation Analysis
8. Findings Development
9. Reporting

The forensic image was validated prior to examination using cryptographic hashing to ensure evidence integrity remained intact throughout the investigation.

---

# Tools Used

| Tool | Purpose |
|--------|----------|
| Autopsy 4.22.1 | Digital forensic analysis |
| PowerShell Get-FileHash | Evidence validation |
| Browser Artifact Examination | User activity reconstruction |
| Excel | Event correlation |
| GPX Data Review | Route reconstruction |
| Communication Analysis | Message examination |

---


# Phase 1: Evidence Integrity Verification

Before beginning analysis, I verified the integrity of the forensic image using both SHA-256 and MD5 hashing.

### Evidence

![Hash Verification](Evidence/01-Hash-Verification.png)

### Observation

The calculated hash values matched the reference values supplied with the evidence.

### Significance

This confirmed that the evidence image had not been altered and could be relied upon throughout the examination.

---

# Phase 2: Forensic Acquisition Validation

I created a new Autopsy case and ingested the forensic image.

### Evidence

![Autopsy Case Creation](Evidence/02-Autopsy-case-creation.png)

![Autopsy Interface](Evidence/03-autopsy-case-interface.png)

### Observation

The evidence image loaded successfully and all file system artefacts were accessible for analysis.

### Significance

This established the foundation for all subsequent examinations.

---

# Phase 3: Maintenance Status Manipulation

One of the primary objectives was determining whether the aircraft was genuinely airworthy before departure.

### Evidence

![Original Status](Evidence/04-bell-412-original-status.png)

![Maintenance Logs](Evidence/05-bell-412-maintenance-logs.png)

![Audit Logs](Evidence/06-bell-412-audit-logs.png)

### Findings

I identified evidence indicating that the maintenance release status was modified.

The original maintenance record indicated:

> AIRCRAFT NOT SERVICEABLE

A subsequent version reflected:

> CLEARED FOR FLIGHT

Audit artefacts attributed the modification to the account:

> kwame.adu

### Significance

This established that a critical maintenance decision was altered before departure.

---

# Phase 4: Component Verification

I compared the installed gearbox oil-pressure sensor assembly against supporting documentation.

### Evidence

![Component Register](Evidence/08-maintenance-components.png)

![Serial Number](Evidence/09-installed-component-serial-number.png)

![Serial Number Closeup](Evidence/10-installed-component-serial-close-up.png)

![Certificate](Evidence/11-component-certificate.png)

![Supplier Invoice](Evidence/12-supplier-invoice.png)

![Component Register](Evidence/13-component-register.png)

### Findings

A discrepancy existed between:

- Installed component serial number
- Certification documentation
- Supplier invoice records

### Significance

The inconsistency raised concerns regarding component traceability and airworthiness compliance.

---

# Phase 5: Concealment Activity

I reviewed browser activity occurring shortly after maintenance records were altered.

### Evidence

![Browser History](Evidence/14-browser-history.png)

### Findings

Browser activity revealed searches associated with:

- File removal
- Log deletion
- Evidence cleanup
- Activity concealment

### Significance

The timing of these searches shortly after the maintenance status modification was notable and potentially indicative of attempts to conceal prior activity.

---

# Phase 6: USB Device Examination

I examined a recovered Kingston USB storage device.

### Evidence

![USB Device](Evidence/15-usb-backup-drive.png)

![Recovered Files](Evidence/16-usb-deleted-recovered.png)

![SetupAPI](Evidence/17-usb-setupapi.png)

![USB Connections](Evidence/18-usb-connections.png)

### Findings

The device contained recovered deleted files associated with maintenance records and historical documentation.

USB connection artefacts corroborated prior use on the maintenance workstation.

### Significance

The recovered files preserved earlier versions of maintenance documentation that contradicted the final approved release status.

---

# Phase 7: Flight Data Reconstruction

I analysed FDR, telemetry and HUMS datasets to reconstruct the aircraft's final flight.

### Evidence

![FDR](Evidence/19-fdr-parsed.png)

![Telemetry](Evidence/20-flight-telementary.png)

![HUMS](Evidence/21-hums-data.png)

![FDR](Evidence/22-fdr-parsed-01.png)

![Telemetry](Evidence/23-flight-telementary-01.png)

![FDR](Evidence/24-fdr-parsed-02.png)

![Telemetry](Evidence/25-flight-telementary-02.png)

![HUMS](Evidence/26-hums-data-01.png)

### Findings

The data demonstrated:

1. Increasing gearbox temperature
2. Escalating vibration levels
3. Progressive degradation
4. Critical oil-pressure loss
5. Loss of aircraft control

### Significance

These observations aligned with a progressive mechanical failure rather than a sudden catastrophic event.

---

# Phase 8: Communication Analysis

I reviewed communications between engineering, operations personnel and flight crew.

### Evidence

![Engineer Phone](Evidence/28-engineer-phone.png)

![Engineer Messages](Evidence/29-engineer-phone-messages.png)

![Pilot Messages](Evidence/30-pilot-messages.png)

### Findings

Communications indicated awareness of recurring gearbox concerns before the aircraft departed.

### Significance

The evidence suggested that known maintenance concerns existed before the aircraft was released for flight.

---

# Phase 9: Cockpit Voice Recorder Correlation

### Evidence

![CVR Transcript](Evidence/27-cvr-transcript.png)

### Findings

Crew discussions referenced:

- Rising gearbox temperature
- Oil pressure concerns
- Increasing vibration

### Significance

The CVR evidence independently corroborated findings from FDR and HUMS analysis.

---

# Phase 10: Route Deviation Assessment

### Evidence

![ATC Events](Evidence/31-atc-events.png)

![Weather Routes](Evidence/32-weather-routes.png)

![Weather Briefing](Evidence/33-weater-briefing.png)

![Planned Route](Evidence/34-planned-routes.png)

![GPS Plot](Evidence/35-gpx-location-plot.png)

### Findings

I compared:

- Planned route
- Actual GPS track
- Weather conditions
- ATC communications

### Conclusion

The route deviation appeared consistent with weather avoidance and operational safety considerations.

No evidence suggested that the deviation itself contributed directly to the mechanical failure.

---

# Final Conclusion

Based on the totality of evidence examined, I concluded that the Bell 412 crash was preceded by a progressive gearbox-related mechanical failure that was reflected in maintenance records, personnel communications, flight telemetry, HUMS data and cockpit voice recordings.

The investigation also identified maintenance record alterations, component documentation discrepancies, recovered deleted files, and browser activity potentially indicative of evidence concealment.

While the route deviation was initially considered a potential contributing factor, correlation of GPS data, weather information and ATC communications indicated that it was a legitimate operational response and not the primary cause of the accident.

The strongest evidentiary support points toward a known maintenance concern that remained unresolved before the aircraft was released for flight.

**CHECKOUT REPORT FOLDER FOR FULL DETAILED REPORT**

---

## Author

**Philip Oppong Adanse**

Digital Forensics & Incident Response (DFIR)
Hive Consult

