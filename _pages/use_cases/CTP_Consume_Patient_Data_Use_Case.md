---
title: Consume Patient Data Use Case
sidebar: overview_sidebar
keywords: use_case
permalink: CTP_Consume_Patient_Data_Use_Case.html
toc: true
folder: use_cases
---
{% include note-furtherupdates.html %}


# 1   Introduction
Consume Patient Record Data

Type:   System Use Case

Level:   Sea Level (Goal obtained by a single actor in a single IT session, mid-level business process with sub-processes).

## 1.1 Business Context

### 1.1.1   Brief Description
The Clinical Triage Platform (CTP) programme seeks to improve the triaging capability in Urgent and Emergency Care (UEC) settings by providing tools and services to support next generation triaging capability better suited to address individual patient needs. Patients are currently triaged and assessed without a view of their medical history, leading to triage that is said to be too generic. In order to triage patients effectively and efficiently, the UEC Encounter Management System (EMS) and any Clinical Decision Support System (CDSS) it uses need to consider and consume patient data from various sources.

The patient data could come from any number of national or local sources which link in with patient care record systems providing information on all aspects of a patient’s medical history which might be relevant at different stages throughout the patient’s UEC encounter. In this use case we propose that EMS and CDSS will consume available patient information from any source which meets the standards and specifications defined by the CTP programme, and in the Pre-Conditions in Section 1.4, and will comply with the General Data Protection Regulation (GDPR).

The clinical data consumed by the EMS will be transient, as patient medical histories may change from day to day. Therefore, there would be no requirement or benefit in holding patient data within the system as the patient’s medical condition can change quickly and the data will become out of date. This use case is therefore only concerned with real time access of the patient’s medical information, at the point of triage (including self-triage and clinical triage) and clinical consultation.

### 1.1.2   Business Goals and Benefits
Current UEC Service Providers have raised the requirement to access patient data during triage. They have stated that the service and patients would benefit greatly from the EMS and CDSS having access to the patient’s medical history to help understand the needs of the individual within the collective patient population. Having patients personal medical history populated in or consumed by the CDSS will promote the delivery of appropriate disposition more quickly than at present.

The FYFV states that the patient population in England is too diverse for a ‘one size fits all’ care model to apply everywhere, and that the NHS has to keep up with changes in patient healthcare needs and preferences. This can be achieved by personalising the provision of care by using all available information about the patient.

There are many aspects to patient care, and accordingly there may be patients with many different types of records about their care. These could include hospital discharge summary, pathology test results, and information regarding diagnosed chronic conditions and the related management or treatment plans.

Due to the nature of urgent care especially in the 111 and IUC CAS space, clinicians and call handlers fielding calls from an ever-changing base of patients will not be able to learn each patient’s full medical history within the brief time of the ad-hoc UEC encounter. Discovery work though the CTP programme has shown that an intelligent responsive triage system that can consume the patient data could address this shortcoming, supporting each patient’s journey through an intelligent automated consideration of the patient’s medical history and improve the ability to provide personalisation of triage for each patient interaction.

By allowing the system to consume patient data in a meaningful way, the burden for clinicians to wade thought lengthy patient records and for call handlers to ask a multitude of questions could be alleviated. A system that can accept patient records as input, apply some logic to it and subsequently modify the clinical assessment of the patient is anticipated to have the following benefits:
-   A more appropriate disposition will be recommended.
-   Reduction in risk of under-triage and over-triage.
-   Optimise the sign-posting of patients to the most appropriate end point taking into consideration patient specific healthcare history and current concerns.
-   Non-Clinical staff will spend less time on triage, by utilising automated data consumption to better inform the triage logic, e.g. triage questions can be automatically answered and or skipped where it is clinically appropriate and safe to do so based on the available patient record data.
-   Clinicians will be better equipped to consult and complete UEC encounters over the phone when supported by automated retrieval and consumption of patient record data.
-   Support the consult and complete model; there would be little or no need to pass patients between clinicians or between settings to clarify their symptoms, as the CDSS would be able to triage the current concern while considering any underlying patient conditions and comorbidities.
-   Improved patient experience driven by the understanding and considering each individual and their needs, while meeting their expectations by using their health and care information to their benefit.

### 1.1.3   Business Area
The business area being modelled in this use case is the consumption of patient health and social care data by systems that support decision making in UEC, a key output of the Personalised Triage workstream of the CTP programme. The use case relates to personalisation of the patient journey. Some elements of triage, clinical consultation and treatment decisions can be supported by the consumption of patient data as explained in this use case. This use case is dependent on wider CTP technical interoperability requirements and standards to facilitate local and national access of patient records in order to effectively support patients across the nation.
### 1.1.4   System under Design (SuD)
One or more CDSS used by the EMS will support Clinicians and Non-Clinicians in assessing patient needs, taking into consideration known facts about the patient’s health. The personalisation can also to be applied to CDSS that support self-triage tools. The CDSS will primarily need access to patient information held on electronic patient care record systems. The EMS, Self-Triage tools and patient care record systems will need to communicate in a manner that enables access to patient data in a format that can be consumed by the CDSS, resulting in some useful output; such as:
-   System generated alerts flags indicating potential risks relating to the patient’s health (e.g. indicating that a patient has a long-term condition that needs to be considered in their UEC encounter).
-   Automatic answering or pre-populating answers to questions within triage paths by automatically retrieving and applying clinically coded data from the patient’s care records.  Depending on the User skill-set or clinical safety rules around the EMS, further verification of the data may be required/supported.

Using patient data to improve triage is not a new concept with some 111 service providers having previously provided patient data to their clinicians for triage purposes. Data sharing between healthcare service providers in UIC has been achieved in the past but it has been limited to local solutions. The CTP approach is unique in that it is an endeavour to provide EMS and CDSS integration with patient data sets on multiple levels both nationally and locally, and it also introduces the automated consumption of patient data by the CDSS.
### 1.1.5   Assumptions
-   System suppliers should use a standardised mechanism to identify patients, it is anticipated that the systems will use the Personal Demographics Service (PDS) to uniquely identify the patient and link them to their available care records.
-   Data sharing will be facilitated at national level.
-   Rules in the integration service must be respected by the EMS, e.g. sealed and sensitive records will not be shared, but the system will be made aware that they exist.
-   The future UEC encounter management systems will support the use of more than one CDSS in any service setting to support specialist triage and clinical consultation needs.
-   The request for patient data could come from any one of the various CDSS in use in UEC settings, therefore structured data provided must conform to standards included in the CTP specifications.
-   Data will conform to agreed terminology standards and a standard Health information model.
-   GPs will move to SNOMED CT by end of 2018, and other care settings will follow suit.

## 1.2 Actors

### 1.2.1   Primary Actors
-   System User (Clinician, Non-Clinician, Patient in Self-Triage)

### 1.2.2   Secondary Actors
-   Patient (As self or Patient Proxy e.g. parent, carer etc.)
-   Care Record System

## 1.3 Trigger
Patient data will be sought by the CDSS via the EMS at one or many points during a patient’s UEC encounter. For example, the CDSS may include questions within its triage logic about aspects of the patient’s medical history which is relevant to the patient’s presenting complaint or reason for contact. The EMS will automatically trigger calls to the relevant APIs and retrieve the patient data for automated consumption where appropriate.

## 1.4 Pre-Conditions
-   Patient has gone through identification verification including retrieving their NHS Number.
-   Where the patient is using a self- triage tool, the tool will have verified the patient’s identity through some self-identification protocols.
-   The healthcare professional is engaged in patient triage at the point in time when the medical history is required; talking to a patient or their representative.
-   The healthcare professional has relevant access and permission to access the patient’s record.
-   A Data-Sharing Agreement exists between the UEC Provider and the Care Record provider.
-   Consent to access the patient Care Record has been obtained either during this patient journey or from pre-arranged authorisation e.g. patient has opted into record sharing options at GP record level, i.e. UEC access to patient records has been pre-authorised in accordance with applicable legislation and (GDPR).
-   Information received from the Care Record system is structured, or can be structured following transformation, to a pre-defined specification.

## 1.5 Post-Conditions
### 1.5.1   On Success
-   Structured patient data is retrieved and consumed by the CDSS. The patient data is used to achieve the following functionality within the CDSS and the EMS:
  - Automated pre-population of data fields.
  - Automatic answering of questions.
  - Supporting local policy; e.g. triggering of system rules and alerts for actions such as re-routing or escalation of patient cases for clinical consultation.
  - Supporting local standard operating procedures for condition management, e.g. chronic condition management, and medication reviews.
-   Access and use of the data is recorded.
-   In the case of non-clinical triage, the triage journey is completed with the aid of the patient data, and the patient is referred to another service (Disposition) or transferred for further clinical assessment (Consultation).
-   In the case of clinical assessment, the clinician will be granted access to information from the patient care record data, and supported by data consumption, e.g. flags, in their clinical decision making until the assessment is completed, or until the clinician transfers the patient onward to another care setting.

### 1.5.2   On Failure:
-   Triage continues without consideration of the patient data.
-   The reason for failure is displayed to the EMS system user, with an appropriate and informative error message.
-   A declined or failed request for access to the patient data is recorded.

### 1.5.3   Guaranteed:
-   The patient’s need will be assessed, with or without the use of their record data.
-   Attempts to access and use of the data are audited, whether they resulted in success or failure, in accordance with GDPR.


## 1.6 ‘Includes’ Use Cases
-   Access Patient Record << includes >> Obtain Patient Consent.
-   Consume Patient Care Record Data << includes >> Call integration API.
-   Perform Personalised Triage Assessment << includes >> Consume Patient Care Record Data.
-   Perform Personalised Clinical Consultation << includes >> Consume Patient Care Record Data.

## 1.7 ‘Extends’ Use Cases
-   Consume Patient Care Record Data << extends >> Access Patient Record.

## 1.8 Local View Use Case Diagram

<p style="text-align:center;"><img src="images/ctp_consume_patient_data_use_case_local_view.png" alt="Tasks" title="View Results Screen" style="width:75%"></p>

` Figure 1 - Use Case Consume Patient Data `


# 2   Flow of Events

<p style="text-align:center;"><img src="images/ctp_consume_patient_data_use_case_event_flow.png" alt="Tasks" title="View Results Screen" style="width:75%"></p>

`Figure 2: Input Data Sequence Flow`

## 2.1 Basic Flow

<table>
  <tr>
    <th colspan="3">Flow Identifier:  System Driven Personalisation</th>
  </tr>
  <tr>
    <td>Step</td>
    <td>User Action</td>
    <td>System Response (optional)</td>
  </tr>
  <tr>
    <td>Trigger</td>
    <td>User conducts triage/consultation and reaches a point where the EMS determines thatclinical data about the patient’s history is required.</td>
    <td><ul><li>Initiate call to a “Get Records” API passing relevantcredentials and a patient identifier (e.g. NHS Number).</li></ul> </td>
  </tr>
  <tr>
    <td>1</td>
    <td>Begintriage or consultation following the standard operating procedures.</td>
    <td><ul>

    <li>       Call an integration API to locate and retrieve patient data</li><li>       Retrieve and apply structured data items to personalise thetriage.</li><li>       Update triage logic based on patient data if applicable, e.g.mitigate risk of over-triage or under-triage.</li><li>       Generate applicable patient risk flags and alerts to display to user.</li>
       </ul></td>
  </tr>
  <tr>
    <td>2</td>
    <td>PerformPersonalised Triage / Consultation following the standard operatingprocedures.Acknowledgesystem responses and the relevant updates using patient data. </td>
    <td><ul><li>       Dynamically consume patient data in triage logic, in conjunctionwith responses provided by the patient and healthcare professional staff duringtriage/consultation.</li><li>       Automatically answer questions using available patient data andskip ahead to the next question.</li><li>       Auto complete questions using available patient data, andclearly reflect these actions for consideration by clinically trainedusers.  </li><li>       Raise flags and alerts and present relevant patient informationas and when required.</li><li>       Provide clear indication that the information was obtained fromthe patient record, including provenance.</li></ul></td>
  </tr>
  <tr>
    <td>3</td>
    <td>Usercompletes triage/consultation supported by automated consumption of patientdata by the EMS and CDSS.</td>
    <td><ul><li>       Integration links to sources of patient data are terminated.</li></ul></td>
  </tr>
  <tr>
    <td>End</td>
    <td>Use Case Ends</td>
    <td> </td>
  </tr>
</table>

## 2.2 Alternative Flow - 1a

<table>
  <tr>
    <th colspan="3">Flow Identifier:  1a - Patient record not found (New Patients, incorrect patient registration, invalid NHS number, record not shared…etc.)</th>
  </tr>
  <tr>
    <td>Step</td>
    <td>User Action</td>
    <td>System Response</td>
  </tr>
  <tr>
    <td>1.a</td>
    <td>None</td>
    <td>EMSfails to locate any patient data or records pertinent to the current triage.
    <ul><li>Provide feedback that the patient records could not be found/records found are empty etc.</li>
    <li>Integration links to sources of patient data are terminated.</li></ul></td>
  </tr>
  <tr>
    <td>2.a</td>
    <td>Acknowledge that no patient data was returned. Manually capture responses to the assessment questions relating to patient clinical history. Continue following the standard operating procedures.</td>
    <td><ul><li>Record the manually captured responses.</li>
    <li>Clearly indicate where answers to questions that could have been completed using data from the patient record have been captured manually.</li></ul></td>
  </tr>
  <tr>
    <td>3.a</td>
    <td>Usercompletes triage/consultation using manually captured input only.</td>
    <td><li>None</li></td>
  </tr>
  <tr>
    <td>On Exit</td>
    <td>Use Case Ends</td>
    <td> </td>
  </tr>
</table>



## 2.3 Alternative Flow - 2b
<table>
  <tr>
    <th colspan="3">Flow Identifier:  Patient Record has been found but is not accessible</th>
  </tr>
  <tr>
    <td>Step</td>
    <td>User Action</td>
    <td>System Response</td>
  </tr>
  <tr>
    <td>1.b</td>
    <td>None</td>
    <td>The EMS locates the record, but the record is not accessible, e.g. sealed records.</td>
  </tr>
  <tr>
    <td>2.b </td>
    <td>Acknowledge the system response. Continue following the standard operating procedures.</td>
    <td><ul><li>Records that record could not be accessed.</li>
    <li>Alert the user that patient records are not accessible.</li>
    <li>Then close integration session.</li></ul></td>
  </tr>
  <tr>
    <td>3.b</td>
    <td>User completes triage/consultation using manually captured input only.</td>
    <td><ul><li>None</li></ul></td>
  </tr>
  <tr>
    <td>On Exit</td>
    <td>Use Case Ends</td>
    <td> </td>
  </tr>
</table>

## 2.4 Exception Flows
<table>
  <tr>
    <th colspan="3">Flow Identifier:  Connections Disrupted</th>
  </tr>
  <tr>
    <td>Step</td>
    <td>User Action</td>
    <td>System Response</td>
  </tr>
  <tr>
    <td>1.c</td>
    <td>None</td>
    <td>The EMS connects to the data source but loses the connection before the data can be accessed and consumed by the EMS and CDSS.</td>
  </tr>
  <tr>
    <td>2.c</td>
    <td>Acknowledge the system response. Continue following the standard operating procedures.</td>
    <td>Alert user that the connection has been disrupted and attempt reconnection.  Alert the user on successful reconnection. If the user completes the triage/consultation before the connection is re-established, the EMS must abandon attempts to reconnect to the data source. </td>
  </tr>
  <tr>
    <td>3.c</td>
    <td>User completes triage/consultation using manually captured input only.</td>
    <td>If a re-connection was successful, close the close integration session.</td>
  </tr>
  <tr>
    <td>On Exit</td>
    <td>Use Case Ends</td>
    <td> </td>
  </tr>
</table>

# 3   Activity Diagram

<p style="text-align:center;"><img src="images/ctp_consume_patient_data_use_case_activity_diagram.png" alt="Tasks" title="View Results Screen" style="width:75%"></p>
`Figure 3 – Input Data Consumption Activity Diagram`

# 4   Entity Diagrams

<p style="text-align:center;"><img src="images/ctp_consume_patient_data_use_case_entity_diagram.png" alt="Tasks" title="View Results Screen" style="width:75%"></p>
`Figure 4 – Entity Relationship Diagram`

# 5   Data Items
Of the many data items that could be pulled from the patient records, the following have been identified, through CTP engagement with Clinicians in UEC as useful and relevant to triage and patient assessment in a UEC setting:
-   Top six (rated as most important by Clinicians):
    -   Allergies / Adverse Reactions
    -   Care Plans
    -   Child Protection/Adult Safeguarding information
    -   Conditions/Problems
    -   DNACPR decisions/ End of life Care Plan
    -   Medications/ Prescriptions
-   Other relevant patient information:
    -   Admission Avoidance Notes
    -   Appointments
    -   Communication preferences
    -   Reasonable Adjustments for Disability Needs
    -   Electronic Frailty Index (eFI)
    -   Encounters
    -   Family history
    -   Immunisations
    -   Investigations, Diagnostics and Procedures
    -   Referrals
    -   Vital Signs
    -   Point of Care Testing
    -   Elected pharmacy
    -   Female Genital Mutilation (FGM)
    -   Social Circumstances

# 6   Information Items
<table>
  <tr>
    <th>Ref<br></th>
    <th>Title<br></th>
    <th>Link<br></th>
  </tr>
  <tr>
    <td></td>
    <td>Integrated Urgent Care Service Specification</td>
    <td><a href="https://www.england.nhs.uk/wp-content/uploads/2014/06/Integrated-Urgent-Care-Service-Specification.pdf">https://www.england.nhs.uk/wp-content/uploads/2014/06/Integrated-Urgent-Care-Service-Specification.pdf</a></td>
  </tr>
  <tr>
    <td></td>
    <td>NHS Digital data dictionary</td>
    <td><a href="http://www.datadictionary.nhs.uk">http://www.datadictionary.nhs.uk</a></td>
  </tr>
</table>



# 7   Business Rules

<table>
  <tr>
    <th>Ref</th>
    <th>Title</th>
    <th>Link</th>
  </tr>
  <tr>
    <td> </td>
    <td>Guideto the General Data Protection Regulation (GDPR)</td>
    <td><a href="https://ico.org.uk/for-organisations/guide-to-the-general-data-protection-regulation-gdpr/">https://ico.org.uk/for-organisations/guide-to-the-general-data-protection-regulation-gdpr/</a> </td>
  </tr>
  <tr>
    <td> </td>
    <td>Onlyauthorized clinicians can trigger the CDSS to access and consume GP heldPatient Data.</td>
    <td><a href="https://ico.org.uk/for-organisations/guide-to-the-general-data-protection-regulation-gdpr/">https://www.england.nhs.uk/contact-us/pub-scheme/pol-proc/</a></td>
  </tr>
  <tr>
    <td> </td>
    <td>PatientData may only be viewed and utilized in direct patient care</td>
    <td><a href="https://ico.org.uk/for-organisations/guide-to-the-general-data-protection-regulation-gdpr/">https://www.england.nhs.uk/contact-us/pub-scheme/pol-proc/</a></td>
  </tr>
  <tr>
    <td> </td>
    <td>Patientconsent must be obtained before the system can access and consume patientinformation.</td>
    <td><a href="https://ico.org.uk/for-organisations/guide-to-the-general-data-protection-regulation-gdpr/">https://www.england.nhs.uk/contact-us/pub-scheme/pol-proc/</a></td>
  </tr>
  <tr>
    <td> </td>
    <td>NHSEngland Data Protection Policy</td>
    <td><a href="https://ico.org.uk/for-organisations/guide-to-the-general-data-protection-regulation-gdpr/">https://www.england.nhs.uk/wp-content/uploads/2016/12/data-protection-policy-v3-1.pdf</a> </td>
  </tr>
</table>