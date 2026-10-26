# 3GPP (3gpp)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

3GPP (the 3rd Generation Partnership Project) is the global standards partnership that writes the technical specifications for mobile networks — GSM, UMTS, LTE, 5G and the ongoing 6G work — through seven regional Organizational Partners (ARIB, ATIS, CCSA, ETSI, TSDSI, TTA and TTC) and a membership of operators, vendors and chipset makers. It is not a service provider and sells nothing to developers; it sits at the very top of the telecom value chain, defining the network functions that every mobile operator on earth deploys and that every CPaaS aggregator ultimately resells. Its API posture is unusually open for a standards body: all 3GPP specifications are published free of charge with no membership or login, and since Release 15 the RESTful Service-Based Architecture, the SCEF/NEF northbound exposure APIs and the SA5 management services have been published as machine-readable OpenAPI 3.0 YAML in a public GitLab instance at forge.3gpp.org. What 3GPP does not run is a developer programme — there is no portal, no key, no sandbox and no callable endpoint; the specifications describe interfaces that operators instantiate, and the developer-facing abstraction over them is CAMARA and GSMA Open Gateway, not 3GPP itself.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/3gpp/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/3gpp/refs/heads/main/apis.yml)

## Tags

- Telecommunications
- Global
- Standards
- Standards Body
- Network APIs
- 5G
- Network Exposure
- NEF
- SCEF
- CAPIF
- Service Based Architecture
- OpenAPI
- OSS
- Network Functions
- 6G

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## Developer Surface — an honest reading

3GPP runs no developer portal. `developer.3gpp.org`, `developers.3gpp.org` and `docs.3gpp.org` do not resolve; `api.3gpp.org` returns 404; `www.3gpp.org/developer` returns 200 but is an ordinary CMS content page with no signup, no key, no sandbox and no console. There is nothing to call: every base URL in every specification below is a template (`{apiRoot}`, `{nrfApiRoot}`) because 3GPP defines interfaces that mobile operators instantiate.

What 3GPP does do — and it is the opposite of most standards bodies in telecom — is give everything away. Technical specifications are published free of charge four times a year with no membership and no login (`https://www.3gpp.org/ftp/Specs/archive/` served a full spec ZIP anonymously at review time), and the RESTful APIs inside those specifications are mirrored as machine-readable OpenAPI 3.0 YAML in a public GitLab at [forge.3gpp.org](https://forge.3gpp.org/). Membership buys a vote, not the output.

**116 OpenAPI documents were harvested verbatim** from two public 3GPP Forge repositories and all 116 parse as valid OpenAPI 3.0.0/3.0.1 — 72 from [all/5G_APIs](https://forge.3gpp.org/rep/all/5G_APIs) at `REL-20` (TS 29.122 T8/SCEF, TS 29.222 CAPIF, TS 29.522 5G NEF northbound) and 44 from [sa5/MnS](https://forge.3gpp.org/rep/sa5/MnS) at `Rel-19` (SA5 management services). 214 paths in total; 43 documents declare OpenAPI `callbacks` (the subscribe/notify pattern that carries network events); 63 declare an OAuth 2.0 client-credentials security scheme with an NRF-issued token URL.

### CAMARA posture

**Underlying standard, not an implementer.** 3GPP publishes no CAMARA API and exposes nothing callable. It writes the layer beneath: CAMARA's Quality on Demand abstracts 3GPP `TS29122_AsSessionWithQoS`, and the device location/status families abstract `TS29122_MonitoringEvent` — both harvested here as the underlay, not as CAMARA implementations. The only CAMARA reference on 3gpp.org is a first-party statement that CAPIF is designed to host non-3GPP APIs "defined by other SDO or consortiums such as ETSI ISG MEC, TM Forum, CAMARA, etc." 3GPP is not a GSMA Open Gateway participant — Open Gateway is an operator commitment programme, and GSMA sits in 3GPP as a Market Representation Partner, not one of the seven Organizational Partners (ARIB, ATIS, CCSA, ETSI, TSDSI, TTA, TTC). CIBA does not appear anywhere in the harvested specifications; 3GPP's consent mechanism is CAPIF RNAA (Resource owner-aware Northbound API Access, Rel-18).

## APIs

All 116 entries below point at a specification 3GPP publishes openly. None is a hosted, callable service.

### TS 28.104 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.104/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.104/)

- **Mda Nrm** — [OpenAPI](openapi/3gpp-ts28104-mdanrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28104_MdaNrm.yaml)
- **Mda Report** — [OpenAPI](openapi/3gpp-ts28104-mdareport.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28104_MdaReport.yaml)

### TS 28.105 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.105/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.105/)

- **Ai Ml Nrm** — [OpenAPI](openapi/3gpp-ts28105-aimlnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28105_AiMlNrm.yaml)

### TS 28.111 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.111/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.111/)

- **Fault Notifications** — [OpenAPI](openapi/3gpp-ts28111-faultnotifications.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28111_FaultNotifications.yaml)  
  `{notificationRecipientAddress}`
- **Fault Nrm** — [OpenAPI](openapi/3gpp-ts28111-faultnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28111_FaultNrm.yaml)  
  `{MnSRoot}/FaultSupervisionMnS/{MnSversion}`

### TS 28.310 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.310/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.310/)

- **Energy Information Nrm** — [OpenAPI](openapi/3gpp-ts28310-energyinformationnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28310_EnergyInformationNrm.yaml)

### TS 28.312 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.312/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.312/)

- **Intent Expectations** — [OpenAPI](openapi/3gpp-ts28312-intentexpectations.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28312_IntentExpectations.yaml)
- **Intent Nrm** — [OpenAPI](openapi/3gpp-ts28312-intentnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28312_IntentNrm.yaml)

### TS 28.317 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.317/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.317/)

- **Ran Sc Nrm** — [OpenAPI](openapi/3gpp-ts28317-ranscnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28317_RanScNrm.yaml)

### TS 28.318 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.318/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.318/)

- **Dso Nrm** — [OpenAPI](openapi/3gpp-ts28318-dsonrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28318_DsoNrm.yaml)

### TS 28.319 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.319/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.319/)

- **Msac Nrm** — [OpenAPI](openapi/3gpp-ts28319-msacnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28319_MsacNrm.yaml)

### TS 28.531 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.531/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.531/)

- **NS Prov Mn S** — [OpenAPI](openapi/3gpp-ts28531-nsprovmns.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28531_NSProvMnS.yaml)  
  `{MnSRoot}/NSProvMnS/{MnSVersion}`
- **NSS Prov Mn S** — [OpenAPI](openapi/3gpp-ts28531-nssprovmns.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28531_NSSProvMnS.yaml)  
  `{MnSRoot}/NSSProvMnS/{MnSVersion}`

### TS 28.532 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.532/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.532/)

- **File Data Reporting Mn S** — [OpenAPI](openapi/3gpp-ts28532-filedatareportingmns.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28532_FileDataReportingMnS.yaml)  
  `{MnSRoot}/fileDataReportingMnS/{MnSVersion}`
- **Heartbeat Ntf** — [OpenAPI](openapi/3gpp-ts28532-heartbeatntf.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28532_HeartbeatNtf.yaml)
- **Perf Mn S** — [OpenAPI](openapi/3gpp-ts28532-perfmns.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28532_PerfMnS.yaml)  
  `{root}`
- **Prov Mn S** — [OpenAPI](openapi/3gpp-ts28532-provmns.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28532_ProvMnS.yaml)  
  `{MnSRoot}/ProvMnS/{MnSVersion}/{URI-LDN-first-part}`
- **Streaming Data Mn S** — [OpenAPI](openapi/3gpp-ts28532-streamingdatamns.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28532_StreamingDataMnS.yaml)  
  `{MnSRoot}/StreamingDataReportingMnS/{MnSVersion}`

### TS 28.536 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.536/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.536/)

- **Cosla Nrm** — [OpenAPI](openapi/3gpp-ts28536-coslanrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28536_CoslaNrm.yaml)

### TS 28.538 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.538/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.538/)

- **Edge Nrm** — [OpenAPI](openapi/3gpp-ts28538-edgenrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28538_EdgeNrm.yaml)

### TS 28.541 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.541/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.541/)

- **5 Gc Nrm** — [OpenAPI](openapi/3gpp-ts28541-5gcnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28541_5GcNrm.yaml)
- **Nr Nrm** — [OpenAPI](openapi/3gpp-ts28541-nrnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28541_NrNrm.yaml)
- **Slice Nrm** — [OpenAPI](openapi/3gpp-ts28541-slicenrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28541_SliceNrm.yaml)

### TS 28.550 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.550/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.550/)

- **Perf Meas Job Ctrl Mn S** — [OpenAPI](openapi/3gpp-ts28550-perfmeasjobctrlmns.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28550_PerfMeasJobCtrlMnS.yaml)  
  `{MnSRoot}/PerfMeasJobCtrlMnS/{MnSVersion}`

### TS 28.561 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.561/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.561/)

- **Ndt Nrm** — [OpenAPI](openapi/3gpp-ts28561-ndtnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28561_NdtNrm.yaml)

### TS 28.567 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.567/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.567/)

- **Ccl Nrm** — [OpenAPI](openapi/3gpp-ts28567-cclnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28567_CclNrm.yaml)

### TS 28.572 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.572/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.572/)

- **Plan Management** — [OpenAPI](openapi/3gpp-ts28572-planmanagement.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28572_PlanManagement.yaml)  
  `{MnSRoot}/plan-management/{MnSVersion}`

### TS 28.623 — Management Services (SA5 OAM)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/28_series/28.623/](https://www.3gpp.org/ftp/Specs/archive/28_series/28.623/)

- **Com Defs** — [OpenAPI](openapi/3gpp-ts28623-comdefs.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_ComDefs.yaml)
- **External Data Mgmt Nrm** — [OpenAPI](openapi/3gpp-ts28623-externaldatamgmtnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_ExternalDataMgmtNrm.yaml)
- **Feature Nrm** — [OpenAPI](openapi/3gpp-ts28623-featurenrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_FeatureNrm.yaml)
- **File Management Nrm** — [OpenAPI](openapi/3gpp-ts28623-filemanagementnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_FileManagementNrm.yaml)
- **Generic Nrm** — [OpenAPI](openapi/3gpp-ts28623-genericnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_GenericNrm.yaml)
- **Management Data Collection Nrm** — [OpenAPI](openapi/3gpp-ts28623-managementdatacollectionnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_ManagementDataCollectionNrm.yaml)
- **Mn S Registry Nrm** — [OpenAPI](openapi/3gpp-ts28623-mnsregistrynrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_MnSRegistryNrm.yaml)
- **Pm Control Nrm** — [OpenAPI](openapi/3gpp-ts28623-pmcontrolnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_PmControlNrm.yaml)
- **Qo E Measurement Collection Nrm** — [OpenAPI](openapi/3gpp-ts28623-qoemeasurementcollectionnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_QoEMeasurementCollectionNrm.yaml)
- **Subscription Control Nrm** — [OpenAPI](openapi/3gpp-ts28623-subscriptioncontrolnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_SubscriptionControlNrm.yaml)
- **Threshold Monitor Nrm** — [OpenAPI](openapi/3gpp-ts28623-thresholdmonitornrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_ThresholdMonitorNrm.yaml)
- **Trace Control Nrm** — [OpenAPI](openapi/3gpp-ts28623-tracecontrolnrm.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS28623_TraceControlNrm.yaml)

### TS 29.122 — T8 Northbound APIs (SCEF / 4G–5G capability exposure)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/29_series/29.122/](https://www.3gpp.org/ftp/Specs/archive/29_series/29.122/)

- **As Session With Qo S** — [OpenAPI](openapi/3gpp-ts29122-assessionwithqos.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_AsSessionWithQoS.yaml)  
  `{apiRoot}/3gpp-as-session-with-qos/v1`
- **Chargeable Party** — [OpenAPI](openapi/3gpp-ts29122-chargeableparty.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_ChargeableParty.yaml)  
  `{apiRoot}/3gpp-chargeable-party/v1`
- **Common Data** — [OpenAPI](openapi/3gpp-ts29122-commondata.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_CommonData.yaml)
- **Cp Provisioning** — [OpenAPI](openapi/3gpp-ts29122-cpprovisioning.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_CpProvisioning.yaml)  
  `{apiRoot}/3gpp-cp-parameter-provisioning/v1`
- **Device Triggering** — [OpenAPI](openapi/3gpp-ts29122-devicetriggering.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_DeviceTriggering.yaml)  
  `{apiRoot}/3gpp-device-triggering/v1`
- **ECR Control** — [OpenAPI](openapi/3gpp-ts29122-ecrcontrol.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_ECRControl.yaml)  
  `{apiRoot}/3gpp-ecr-control/v1`
- **GM Dvia MBM Sby MB2** — [OpenAPI](openapi/3gpp-ts29122-gmdviambmsbymb2.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_GMDviaMBMSbyMB2.yaml)  
  `{apiRoot}/3gpp-group-message-delivery-mb2/v1`
- **GM Dvia MBM Sbyx MB** — [OpenAPI](openapi/3gpp-ts29122-gmdviambmsbyxmb.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_GMDviaMBMSbyxMB.yaml)  
  `{apiRoot}/3gpp-group-message-delivery-xmb/v1`
- **Monitoring Event** — [OpenAPI](openapi/3gpp-ts29122-monitoringevent.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_MonitoringEvent.yaml)  
  `{apiRoot}/3gpp-monitoring-event/v1`
- **Msisdn Less Mo Sms** — [OpenAPI](openapi/3gpp-ts29122-msisdnlessmosms.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_MsisdnLessMoSms.yaml)  
  `{apiRoot}`
- **NIDD** — [OpenAPI](openapi/3gpp-ts29122-nidd.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_NIDD.yaml)  
  `{apiRoot}/3gpp-nidd/v1`
- **Np Configuration** — [OpenAPI](openapi/3gpp-ts29122-npconfiguration.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_NpConfiguration.yaml)  
  `{apiRoot}/3gpp-network-parameter-configuration/v1`
- **Pfd Management** — [OpenAPI](openapi/3gpp-ts29122-pfdmanagement.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_PfdManagement.yaml)  
  `{apiRoot}/3gpp-pfd-management/v1`
- **Racs Parameter Provisioning** — [OpenAPI](openapi/3gpp-ts29122-racsparameterprovisioning.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_RacsParameterProvisioning.yaml)  
  `{apiRoot}/3gpp-racs-pp/v1`
- **Reporting Network Status** — [OpenAPI](openapi/3gpp-ts29122-reportingnetworkstatus.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_ReportingNetworkStatus.yaml)  
  `{apiRoot}/3gpp-net-stat-report/v1`
- **Resource Management Of Bdt** — [OpenAPI](openapi/3gpp-ts29122-resourcemanagementofbdt.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29122_ResourceManagementOfBdt.yaml)  
  `{apiRoot}/3gpp-bdt/v1`

### TS 29.222 — CAPIF, the Common API Framework

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/29_series/29.222/](https://www.3gpp.org/ftp/Specs/archive/29_series/29.222/)

- **AEF Security** — [OpenAPI](openapi/3gpp-ts29222-aef-security-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_AEF_Security_API.yaml)  
  `{apiRoot}/aef-security/v1`
- **CAPIF Access Control Policy** — [OpenAPI](openapi/3gpp-ts29222-capif-access-control-policy-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_Access_Control_Policy_API.yaml)  
  `{apiRoot}/access-control-policy/v1`
- **CAPIF Invoker Management** — [OpenAPI](openapi/3gpp-ts29222-capif-api-invoker-management-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_API_Invoker_Management_API.yaml)  
  `{apiRoot}/api-invoker-management/v1`
- **CAPIF Provider Management** — [OpenAPI](openapi/3gpp-ts29222-capif-api-provider-management-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_API_Provider_Management_API.yaml)  
  `{apiRoot}/api-provider-management/v1`
- **CAPIF Auditing** — [OpenAPI](openapi/3gpp-ts29222-capif-auditing-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_Auditing_API.yaml)  
  `{apiRoot}/logs/v1`
- **CAPIF Discover Service** — [OpenAPI](openapi/3gpp-ts29222-capif-discover-service-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_Discover_Service_API.yaml)  
  `{apiRoot}/service-apis/v1`
- **CAPIF Events** — [OpenAPI](openapi/3gpp-ts29222-capif-events-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_Events_API.yaml)  
  `{apiRoot}/capif-events/v1`
- **CAPIF Logging Invocation** — [OpenAPI](openapi/3gpp-ts29222-capif-logging-api-invocation-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_Logging_API_Invocation_API.yaml)  
  `{apiRoot}/api-invocation-logs/v1`
- **CAPIF Open Discover Service** — [OpenAPI](openapi/3gpp-ts29222-capif-open-discover-service-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_Open_Discover_Service_API.yaml)  
  `{apiRoot}/open-api-disc/v1`
- **CAPIF Publish Service** — [OpenAPI](openapi/3gpp-ts29222-capif-publish-service-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_Publish_Service_API.yaml)  
  `{apiRoot}/published-apis/v1`
- **CAPIF Routing Info** — [OpenAPI](openapi/3gpp-ts29222-capif-routing-info-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_Routing_Info_API.yaml)  
  `{apiRoot}/capif-routing-info/v1`
- **CAPIF Security** — [OpenAPI](openapi/3gpp-ts29222-capif-security-api.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29222_CAPIF_Security_API.yaml)  
  `{apiRoot}/capif-security/v1`

### TS 29.512 — Policy Control (PCF)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/29_series/29.512/](https://www.3gpp.org/ftp/Specs/archive/29_series/29.512/)

- **Npcf SM Policy Control** — [OpenAPI](openapi/3gpp-ts29512-npcf-smpolicycontrol.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS29512_Npcf_SMPolicyControl.yaml)  
  `{apiRoot}/npcf-smpolicycontrol/v1`

### TS 29.514 — Policy Authorization (PCF)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/29_series/29.514/](https://www.3gpp.org/ftp/Specs/archive/29_series/29.514/)

- **Npcf Policy Authorization** — [OpenAPI](openapi/3gpp-ts29514-npcf-policyauthorization.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS29514_Npcf_PolicyAuthorization.yaml)  
  `{apiRoot}/npcf-policyauthorization/v1`

### TS 29.520 — Network Data Analytics (NWDAF)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/29_series/29.520/](https://www.3gpp.org/ftp/Specs/archive/29_series/29.520/)

- **Nnwdaf Analytics Info** — [OpenAPI](openapi/3gpp-ts29520-nnwdaf-analyticsinfo.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS29520_Nnwdaf_AnalyticsInfo.yaml)  
  `{apiRoot}/nnwdaf-analyticsinfo/v1`
- **Nnwdaf Events Subscription** — [OpenAPI](openapi/3gpp-ts29520-nnwdaf-eventssubscription.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS29520_Nnwdaf_EventsSubscription.yaml)  
  `{apiRoot}/nnwdaf-eventssubscription/v1`

### TS 29.522 — 5G NEF Northbound APIs (network exposure to third parties)

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/29_series/29.522/](https://www.3gpp.org/ftp/Specs/archive/29_series/29.522/)

- **5 GLAN Parameter Provision** — [OpenAPI](openapi/3gpp-ts29522-5glanparameterprovision.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_5GLANParameterProvision.yaml)  
  `{apiRoot}/3gpp-5glan-pp/v1`
- **ACS Parameter Provision** — [OpenAPI](openapi/3gpp-ts29522-acsparameterprovision.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_ACSParameterProvision.yaml)  
  `{apiRoot}/3gpp-acs-pp/v1`
- **Addressing Param Provision** — [OpenAPI](openapi/3gpp-ts29522-addressingparamprovision.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_AddressingParamProvision.yaml)  
  `{apiRoot}/3gpp-addr-pp/v1`
- **A Io T** — [OpenAPI](openapi/3gpp-ts29522-aiot.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_AIoT.yaml)  
  `{apiRoot}/3gpp-aiot/v1`
- **AKMA** — [OpenAPI](openapi/3gpp-ts29522-akma.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_AKMA.yaml)  
  `{apiRoot}/3gpp-akma/v1`
- **AM Influence** — [OpenAPI](openapi/3gpp-ts29522-aminfluence.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_AMInfluence.yaml)  
  `{apiRoot}/3gpp-am-influence/v1`
- **AM Policy Authorization** — [OpenAPI](openapi/3gpp-ts29522-ampolicyauthorization.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_AMPolicyAuthorization.yaml)  
  `{apiRoot}/3gpp-am-policyauthorization/v1`
- **Analytics Exposure** — [OpenAPI](openapi/3gpp-ts29522-analyticsexposure.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_AnalyticsExposure.yaml)  
  `{apiRoot}/3gpp-analyticsexposure/v1`
- **Applying Bdt Policy** — [OpenAPI](openapi/3gpp-ts29522-applyingbdtpolicy.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_ApplyingBdtPolicy.yaml)  
  `{apiRoot}/3gpp-applying-bdt-policy/v1`
- **ASTI** — [OpenAPI](openapi/3gpp-ts29522-asti.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_ASTI.yaml)  
  `{apiRoot}/3gpp-asti/v1`
- **Cag Info Param Provision** — [OpenAPI](openapi/3gpp-ts29522-caginfoparamprovision.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_CagInfoParamProvision.yaml)  
  `{apiRoot}/3gpp-caginfo-pp/v1`
- **Data Reporting** — [OpenAPI](openapi/3gpp-ts29522-datareporting.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_DataReporting.yaml)  
  `{apiRoot}/3gpp-data-reporting/v1`
- **Data Reporting Provisioning** — [OpenAPI](openapi/3gpp-ts29522-datareportingprovisioning.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_DataReportingProvisioning.yaml)  
  `{apiRoot}/3gpp-data-reporting-provisioning/v1`
- **DNAI Mapping** — [OpenAPI](openapi/3gpp-ts29522-dnaimapping.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_DNAIMapping.yaml)  
  `{apiRoot}/3gpp-dnai-mapping/v1`
- **EAS Deployment** — [OpenAPI](openapi/3gpp-ts29522-easdeployment.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_EASDeployment.yaml)  
  `{apiRoot}/3gpp-eas-deployment/v1`
- **ECS Address** — [OpenAPI](openapi/3gpp-ts29522-ecsaddress.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_ECSAddress.yaml)  
  `{apiRoot}/3gpp-ecs-address/v1`
- **Ecs Address Provision** — [OpenAPI](openapi/3gpp-ts29522-ecsaddressprovision.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_EcsAddressProvision.yaml)  
  `{apiRoot}/3gpp-ecs-address-provision/v1`
- **Group Parameters Provisioning** — [OpenAPI](openapi/3gpp-ts29522-groupparametersprovisioning.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_GroupParametersProvisioning.yaml)  
  `{apiRoot}/3gpp-grp-pp/v1`
- **Ims Event Exposure** — [OpenAPI](openapi/3gpp-ts29522-imseventexposure.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_ImsEventExposure.yaml)  
  `{apiRoot}/3gpp-ims-ee/v1`
- **Ims Param Provision** — [OpenAPI](openapi/3gpp-ts29522-imsparamprovision.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_ImsParamProvision.yaml)  
  `{apiRoot}/3gpp-ims-pp/v1`
- **Ims Session Management** — [OpenAPI](openapi/3gpp-ts29522-imssessionmanagement.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_ImsSessionManagement.yaml)  
  `{apiRoot}/3gpp-ims-sm/v1`
- **IPTV Configuration** — [OpenAPI](openapi/3gpp-ts29522-iptvconfiguration.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_IPTVConfiguration.yaml)  
  `{apiRoot}/3gpp-iptvconfiguration/v1`
- **Lpi Parameter Provision** — [OpenAPI](openapi/3gpp-ts29522-lpiparameterprovision.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_LpiParameterProvision.yaml)  
  `{apiRoot}/3gpp-lpi-pp/v1`
- **MBS Group Msg Delivery** — [OpenAPI](openapi/3gpp-ts29522-mbsgroupmsgdelivery.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_MBSGroupMsgDelivery.yaml)  
  `{apiRoot}/3gpp-mbs-group-msg/v1`
- **MBS Session** — [OpenAPI](openapi/3gpp-ts29522-mbssession.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_MBSSession.yaml)  
  `{apiRoot}/3gpp-mbs-session/v1`
- **MBSTMGI** — [OpenAPI](openapi/3gpp-ts29522-mbstmgi.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_MBSTMGI.yaml)  
  `{apiRoot}/3gpp-mbs-tmgi/v1`
- **MBS User Data Ingest Session** — [OpenAPI](openapi/3gpp-ts29522-mbsuserdataingestsession.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_MBSUserDataIngestSession.yaml)  
  `{apiRoot}/3gpp-mbs-ud-ingest/v1`
- **MBS User Service** — [OpenAPI](openapi/3gpp-ts29522-mbsuserservice.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_MBSUserService.yaml)  
  `{apiRoot}/3gpp-mbs-us/v1`
- **Member UE Selection Assistance** — [OpenAPI](openapi/3gpp-ts29522-memberueselectionassistance.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_MemberUESelectionAssistance.yaml)  
  `{apiRoot}/3gpp-musa/v1`
- **Mo Lcs Notify** — [OpenAPI](openapi/3gpp-ts29522-molcsnotify.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_MoLcsNotify.yaml)  
  `{apiRoot}/3gpp-mo-lcs-notify/v1`
- **MS Event Exposure** — [OpenAPI](openapi/3gpp-ts29522-mseventexposure.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_MSEventExposure.yaml)  
  `{apiRoot}/3gpp-ms-event-exposure/v1`
- **NIDD Configuration Trigger** — [OpenAPI](openapi/3gpp-ts29522-niddconfigurationtrigger.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_NIDDConfigurationTrigger.yaml)  
  `{apiRoot}`
- **PDTQ Policy Negotiation** — [OpenAPI](openapi/3gpp-ts29522-pdtqpolicynegotiation.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_PDTQPolicyNegotiation.yaml)  
  `{apiRoot}/3gpp-pdtq-policy-negotiation/v1`
- **RSLPPI Parameters Provisioning** — [OpenAPI](openapi/3gpp-ts29522-rslppiparametersprovisioning.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_RSLPPIParametersProvisioning.yaml)  
  `{apiRoot}/3gpp-rslppi-pp/v1`
- **Service Parameter** — [OpenAPI](openapi/3gpp-ts29522-serviceparameter.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_ServiceParameter.yaml)  
  `{apiRoot}/3gpp-service-parameter/v1`
- **Slice Param Provision** — [OpenAPI](openapi/3gpp-ts29522-sliceparamprovision.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_SliceParamProvision.yaml)  
  `{apiRoot}/3gpp-slice-pp/v1`
- **Time Sync Exposure** — [OpenAPI](openapi/3gpp-ts29522-timesyncexposure.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_TimeSyncExposure.yaml)  
  `{apiRoot}/3gpp-time-sync/v1`
- **Traffic Influence** — [OpenAPI](openapi/3gpp-ts29522-trafficinfluence.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_TrafficInfluence.yaml)  
  `{apiRoot}/3gpp-traffic-influence/v1`
- **UAV Flight Assistance** — [OpenAPI](openapi/3gpp-ts29522-uavflightassistance.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_UAVFlightAssistance.yaml)  
  `{apiRoot}/3gpp-uav-fa/v1`
- **UE Address** — [OpenAPI](openapi/3gpp-ts29522-ueaddress.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_UEAddress.yaml)  
  `{apiRoot}/3gpp-ue-address/v1`
- **UE Id** — [OpenAPI](openapi/3gpp-ts29522-ueid.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_UEId.yaml)  
  `{apiRoot}/3gpp-ueid/v1`
- **VFL Inference** — [OpenAPI](openapi/3gpp-ts29522-vflinference.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_VFLInference.yaml)  
  `{apiRoot}/3gpp-vfl-inference/v1`
- **VFLNF Discovery** — [OpenAPI](openapi/3gpp-ts29522-vflnfdiscovery.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_VFLNFDiscovery.yaml)  
  `{apiRoot}/3gpp-vfl-nf-discovery/v1`
- **VFL Training** — [OpenAPI](openapi/3gpp-ts29522-vfltraining.yml) · [source](https://forge.3gpp.org/rep/all/5G_APIs/-/raw/REL-20/TS29522_VFLTraining.yaml)  
  `{apiRoot}/3gpp-vfl-training/v1`

### TS 29.571 — 5G Common Data Types

Specification archive: [https://www.3gpp.org/ftp/Specs/archive/29_series/29.571/](https://www.3gpp.org/ftp/Specs/archive/29_series/29.571/)

- **Common Data** — [OpenAPI](openapi/3gpp-ts29571-commondata.yml) · [source](https://forge.3gpp.org/rep/sa5/MnS/-/raw/Rel-19/OpenAPI/TS29571_CommonData.yaml)

## Common Properties

- [Website](https://www.3gpp.org/)
- [Documentation](https://www.3gpp.org/specifications-technologies)
- [SpecificationsArchive](https://www.3gpp.org/ftp/Specs/archive/)
- [Portal](https://portal.3gpp.org/)
- [SourceCode](https://forge.3gpp.org/rep/all/5G_APIs)
- [SourceCode](https://forge.3gpp.org/rep/sa5/MnS)
- [Tools](https://forge.3gpp.org/swagger/tools/parser.html)
- [Blog](https://www.3gpp.org/news-events)
- [LinkedIn](https://www.linkedin.com/company/3gpp)

## Maintainers

- Kin Lane <kin@apievangelist.com>
