# CareGuide 🩺

> A user-friendly healthcare chatbot built with Voiceflow.

---

## Overview

**CareGuide** is a conversational chatbot designed to provide basic healthcare guidance and education. It helps users:
- Understand general health information
- Check symptoms
- Access mental health support
- Find nearby medical facilities

> **Note:** CareGuide does not diagnose conditions. It provides general guidance and encourages users to seek professional medical care when appropriate.

---

## Features

- **Symptom Checker**: Step-by-step guidance to help users understand their symptoms.
- **Mental Health Support**: Empathetic responses for stress, anxiety, and emotional wellbeing, including crisis escalation.
- **Nearby Medical Facilities**: Locates local doctors, pharmacies, hospitals, urgent care centers, and clinics based on the user's location.
- **Emergency Escalation**: Detects high-risk keywords and redirects users to emergency services.
- **Smart Fallback**: Clarifies user intent and presents a menu when input is unclear.
- **Voice Interaction**: CareGuide now supports voice-based interactions. Users can speak to CareGuide and receive spoken responses in return. This feature ensures a natural, conversational experience.
- **Multilingual Support**: CareGuide can communicate in all 11 official South African languages, including English, Zulu, Xhosa, Afrikaans, Sepedi, Setswana, Sesotho, Tsonga, Swati, Venda, and Ndebele. It detects the user's language automatically and responds accordingly.


---

## Safety Measures

CareGuide prioritizes user safety with the following responses:

| Trigger                          | Response                                   |
|----------------------------------|-------------------------------------------|
| Chest pain, trouble breathing    | Immediate emergency escalation            |
| Severe bleeding, stroke signs    | Immediate emergency escalation            |
| Severe allergic reaction         | Immediate emergency escalation            |
| Suicidal intent or overdose      | Crisis hotline + immediate escalation     |
| Concerning or worsening symptoms | Encouragement to seek professional care   |

For mental health requests, CareGuide displays relevant regional crisis hotlines alongside local mental health resources.

---

## Conversation Flow

```plaintext
User opens chat
    └─ Greeting + disclaimer shown
        └─ Intent menu presented
            ├─ Symptom Checker   → Step-by-step symptom flow
            ├─ Mental Health     → Supportive flow + local resources
            ├─ Find Facilities   → Location prompt → search → card results
            └─ Something else    → Clarifying question → re-route
```

If a **high-risk keyword** is detected at any point in the conversation, the flow immediately breaks to the emergency escalation response — regardless of where the user is in the flow.

---

## Communication Style

- Short, clear, step-by-step messages
- One question at a time
- Empathetic and non-judgmental tone
- Plain language — no medical jargon
- Summaries of next steps at the end of flows
- No shaming, blaming, or alarming language

---

## Tools & Integrations

| Tool | Purpose |
|---|---|
| `render_buttons` | Displays intent menu when user intent is ambiguous |
| `knowledge_base_search` | Retrieves chatbot-specific help content 
| `web_search` | Finds nearby medical facilities and regional crisis hotlines |
| `end_conversation` | Gracefully closes the session when the user says goodbye |

> `web_search` is **never** used for diagnosing symptoms or retrieving medical information.

---

## Skills (Playbooks & Workflows)

Skills take priority over the global prompt whenever a user's request matches them.

##  Nearby Facilities Playbook
Triggered when a user asks to find a doctor, pharmacy, hospital, clinic, or any local medical resource.

**Flow:**
1. Ask the user for their general location (city, region, or zip code)
2. Run a web search for relevant nearby facilities
3. Display results as Cards or Carousels with:
   - Facility name and type
   - Address
   - Contact information (where available)
4. Match facility type to the user's need (e.g., pharmacy for medication queries, hospital for urgent concerns)
5. For mental health requests: include nearby mental health clinics/counselors **and** the regional crisis hotline

---


## Data Handling

- CareGuide collects only the **minimum information necessary** to fulfil a request
- Location data is used only to search for nearby facilities
- No sensitive health data is stored or transmitted beyond what the platform requires

---

## Disclaimer

> **CareGuide is not a substitute for professional medical advice, diagnosis, or treatment.** Always seek the advice of a qualified health provider with any questions you may have regarding a medical condition. Never disregard professional medical advice or delay seeking it because of something CareGuide has told you.

---

## Viewing & Editing the Agent
You can view and use the live CareGuide on the link below:
1. https://creator.voiceflow.com/share/69eb12a06698cc0dab2d182e/development

You can import and edit CareGuide directly in Voiceflow:

1. Create a free account at https://www.voiceflow.com/
2. From your dashboard, click **Create Project** → **Import**
3. Upload the `CareGuide_AI_agent.vf` file included in this repository
4. The full conversation flow, prompts, and skills will load into your workspace ready to view or edit

> Changes to the global prompt or instructions should be reflected in the corresponding Voiceflow steps to keep behaviour consistent.

---

## Built With

- Voiceflow https://www.voiceflow.com/ — Conversation design and flow logic