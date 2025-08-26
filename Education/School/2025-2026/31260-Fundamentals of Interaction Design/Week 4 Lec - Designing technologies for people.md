## 1. Cognition

### **Concept**

- Cognition is how the mind **transforms, reduces, elaborates, stores, retrieves, and uses** information to act.
    
- Design goal: **lower mental effort** and **fit how people actually think and work**.
    

---

### **Cognitive capability map (what UI must directly support)**

- _Attention & working memory_
    
    - People can hold only a few “chunks” at once.
        
    - Design: **autocomplete**, **inline hints**, **step-by-step flows**; place information **right where it’s needed**.
        
- _Comprehension_
    
    - Turning data into meaning.
        
    - Design: strong **visual hierarchy** (title → subtitle → body), **plain language**.
        
- _Language (reading/writing)_
    
    - Keep microcopy short and specific; avoid internal jargon.
        
    - Design: buttons use **action verbs** (“Pay”, “Send”, “Save”).
        
- _Calculation – reasoning – decisions_
    
    - Compare, estimate, choose.
        
    - Design: **consistent units**, **clear number formatting**, prefer **tables/charts** over long paragraphs.
        

---

### **Cognitive load**

- _Intrinsic (task difficulty itself)_ — can’t remove, **restructure** it.  
    → Break into steps, show examples, use smart defaults.
    
- _Extraneous (UI-caused burden)_ — **eliminate** it.  
    → Clean layout, whitespace, group related items, drop decorative noise.
    
- _Germane (useful effort)_ — **encourage** at the right time.  
    → In-place visuals, brief A/B comparisons, tooltips that build **chunks** of knowledge.
    

---

### **Attention & preattentive cues**

- Fastest-to-see cues: **size, weight, border, position, direction**.
    
- Design: **one primary focal action** (one CTA), make key numbers **larger/bolder**, use **panels/borders** to group.
    
- Avoid change blindness: state changes must be **clear and immediate** (loading → progress → done), add **sound/vibration** when appropriate.
    

---

### **Memory: recognition > recall**

- _Recognition beats recall_  
    → Use autocomplete, recent items, date pickers, labels close to fields, and a **preview** before confirm.
    
- _Chunking_  
    → Group fields by **task** (Shipping / Payment) and add clear subheadings.
    

---

### **Mental model & conceptual model**

- Users come with a **mental model** (how they think it works).
    
- Provide a consistent **conceptual model** in the UI: names, flows, and icons all tell **one coherent story**.
    
- _Affordance & signifier_
    
    - Affordance: what can be done.
        
    - Signifier: the cue that says it can be done.  
        → Raised button = “pressable”; ellipsis = “more options”.
        

---

### **Choices & feedback**

- **Reduce upfront choices**, reveal more later (**progressive disclosure**).
    
- **Good defaults** (editable) with a short note of what they do.
    
- **Immediate feedback** after every action (visual / audio / haptic) to close the loop.
    
- For long operations: **progress bar + time estimate + cancel** when sensible.
    

---

### **Human error: slips vs. mistakes**

- _Slip (mis-action)_ — right goal, wrong tap.  
    → Separate destructive buttons, prefer **Undo** over constant “Are you sure?”, confirm only for truly destructive acts.
    
- _Mistake (misunderstanding)_ — wrong goal/rule.  
    → Plain language, **feedforward** (“what will happen next”), examples, validation with helpful explanations.
    

---

### **Language & readability**

- Short sentences, familiar words, direct tone (“Delete file?” not formal boilerplate).
    
- **Information scent**: headings and short blurbs that predict what’s inside.
    
- Write **for the task**, avoid fluff.
    

---

### **Multimodal design**

- If eyes/hands are busy: add **voice** or **haptics**; in noisy/quiet contexts: lean on **visuals**.
    
- **Redundant channels** for important messages: at least two (color + label + icon; sound + banner; haptic + toast).
    

---

### **Recommended patterns**

- Task-based grouping; clear hierarchy; generous whitespace.
    
- **Inline hints & inline validation** (format examples; instant errors).
    
- Clear states: skeleton/loading → progress → result; **icon + short text**; brief animations.
    
- **Smart defaults** (remember last address, usual shipping).
    
- **Undo > Are you sure**; **progressive disclosure** for “Advanced”.
    

### **Anti-patterns to avoid**

- Forcing people to **remember codes/IDs** across screens.
    
- **Multiple competing primaries** (2–3 CTAs all loud).
    
- Long text for tiny state changes; **color-only** meaning; **single-channel** messaging in risky contexts.
    

---

### **Quick application examples**

- _Checkout form_
    
    - Labels close to inputs; group “Card / Billing / Shipping”; one primary button; inline validation; “MM/YY” hint.
        
    - After “Pay”: clear progress → success with icon; brief **Undo** window.
        
- _Search & filter_
    
    - Autocomplete (history + suggestions); results show **filter chips**; on apply: short animation + “Filtering by: …” message.
        
- _File upload_
    
    - Skeleton → progress → “Done”; if the user switches tabs: **toast** + optional sound/haptic.
## 2) Perception & the Interaction Loop 

**Core idea**

- Interaction is a **two-way dialogue**. The user **perceives** the interface → forms an intention → **acts**.
    
- The system **detects** the action → processes it → **responds**.
    
- The user then **perceives the response** and continues.
    
- Good design makes this loop **fast, clear, and continuous**.
    

---

**Human side (input and output of people)**

- **Perception channels**: vision, hearing, touch (sometimes smell/taste in niche contexts).
    
- **Effectors (how we act)**: hands/fingers (tap, type, drag), voice (commands), body motion (tilt, gesture).
    
- Design goal: important elements are **easy to notice**; actions are **obvious and effortless**.
    

**System side (how products sense and reply)**

- **Sensors/controls (inputs)**: keyboard, mouse/touch, mic, camera, sliders, buttons, biometrics, motion sensors.
    
- **Displays/outputs**: screen (text, color, motion), audio (tones, speech), haptics (vibration), lights/actuators.
    
- Design goal: pick the **right output channels** for context, and ensure the system **always acknowledges** user actions.
    

---

**Step-by-step loop (with design hooks)**

- **Observe → Interpret**: user perceives the current state.
    
    - Make state **visible**: clear labels, enough contrast, one primary action.
        
- **Intend → Act**: user decides and performs an action.
    
    - Provide **affordances** (looks actionable) and **signifiers** (icons, microcopy). Offer **feedforward** (hint of what will happen).
        
- **System detects → Processes → Responds**: product receives input, updates state.
    
    - Guarantee **immediate acknowledgement** (pressed state, ripple, spinner), then show **progress or result**.
        
- **User perceives response → Continues**: user sees/hears/feels the change.
    
    - Use **redundant cues** (icon + text; sound + banner; haptic + toast) so feedback lands even when attention is divided.
        

---

**Timing benchmarks (to keep the loop alive)**

- ~**100 ms** → feels instantaneous (tap highlight, keypress echo).
    
- ~**1 s** → still feels fluent; show a lightweight progress hint if needed.
    
- **> 2–3 s** → must show **progress bar/estimate** and allow **cancel** if safe.
    
- Rule of thumb: every intentional action should get a **visible reaction within 100–200 ms**.
    

---

**Mapping channels to intent (multimodal design)**

- **Visual** → for dense information, precise status.
    
- **Audio** → for attention-grabbing, eyes-off moments.
    
- **Haptic** → for confirmation without visual demand.
    
- For critical events, use **at least two channels** (e.g., success = checkmark + short tone; error = red banner + vibration).
    
- Avoid relying on **color alone**; always pair with labels or icons.
    

---

**Error-tolerant loop**

- **Slip (mis-action)**: right goal, wrong tap.
    
    - Large targets, separate destructive actions, support **Undo**, reserve confirmation for destructive actions.
        
- **Mistake (misunderstanding)**: wrong goal/rule.
    
    - Use **plain language**, feedforward (“what happens next”), examples, and validations that **explain fixes**.
        
- Never fail silently: always state **what happened** and **what to do next**.
    

---

**Patterns that strengthen the loop**

- **Pressed state + micro-feedback** on every tap/click.
    
- **Inline validation** beside fields; don’t delay errors until the end.
    
- **Skeleton → progress → result**; avoid blank screens.
    
- **Snackbars/toasts** for background tasks (uploads, sync), optionally with subtle sound/haptic.
    
- **Progressive disclosure**: fewer upfront choices; expand as needed.
    

**Anti-patterns (that break the loop)**

- State changes with **no cue**.
    
- **Multiple competing CTAs**, no clear next action.
    
- Important messages in only **one channel** (sound-only or color-only).
    
- Long tasks with **no progress indicator** or **no cancel option**.
    

---

**Mini-examples**

- **File upload**: click “Upload” → button shows pressed state within ≤100 ms → progress bar updates → completion toast + checkmark; if app is backgrounded, add tone/vibration.
    
- **Voice timer**: “Set a 10-minute timer” → immediate confirmation (“Timer set for 10 minutes”) → subtle ring/progress circle → vibration + banner at finish.
    
- **Mobile checkout**: tap “Pay” → button locks + spinner (≤200 ms) → progress with ETA → success screen with order ID + optional **Undo/cancel within 10s**.
## 3. Modes • Modalities • Types

**One-sentence memory aid**

- **Mode** = how the system is **interpreting** the same action right now.
    
- **Modality** = the **channel** you and the system use (see/hear/touch/voice).
    
- **Type** = the **specific way** you act within a channel (tap, drag, speak, type).
    

---

### Mode (the system’s “interpretation setting”)

**Everyday intuition**

- Caps Lock on a keyboard: the same key press yields a different result → that’s a **mode**.
    
- Camera app: **Photo** vs **Video**. Tapping the big button does different things depending on **mode**.
    

**UI examples**

- Editor: **Insert** mode (Delete removes a character) vs **Select** mode (Delete removes the selection).
    
- Maps: default **Pan** vs **Measure** mode (drag pans vs drag draws).
    

**Typical failure: mode error**

- Users think they’re in A but are actually in B → “why did it do that?”
    

**Design tactics**

- Use **as few modes as possible**; prefer **modeless** for common tasks.
    
- Make mode **visible near the action** (toggle, badge, color, icon).
    
- Provide **feedforward**: hint what the action will do _in this mode_.
    
- **Easy escape** (one tap/ESC) and **Undo** for risky actions.
    
- When mode changes, **layout/controls should visibly shift** so users _feel_ the change.
    

**10-second test**

- Hide the title bar. From the working area alone, can you **tell which mode you’re in**? If not, add stronger cues.
    

---

### Modality (the channel of interaction)

**Everyday intuition**

- Order pizza by **phone call** (voice) or via **app** (visual/touch). Same goal, different **channels**.
    

**UI examples**

- Enter an address by **typing** (visual/touch) or by **saying it** (voice).
    
- Confirm completion with **checkmark + text** (visual) and **vibration** (haptic).
    

**Choosing the channel**

- **Visual** for dense/precise info (forms, charts).
    
- **Audio** for attention-grabbing or **eyes-off** moments (driving, cooking).
    
- **Haptic** for subtle **confirmation** without visual demand.
    

**Multimodal principles**

- For important events, use **at least two channels** (e.g., success = checkmark + short tone; error = red banner + vibration).
    
- Don’t rely on **color alone**; pair with labels or icons.
    
- Provide **fallbacks**: if voice fails, show the keyboard; if haptics are off, show a banner.
    

**10-second test**

- Mute audio and partially cover the screen. Is the critical message **still clear**? If not, add redundancy.
    

---

### Type (the specific action within a channel)

**Everyday intuition**

- Opening a door: **press**, **turn**, or **pull**. Same channel (physical action), different **types**.
    

**UI examples**

- **Tap/Click** for primary confirmation.
    
- **Long-press** for secondary options (don’t hide primary functions here).
    
- **Drag & Drop** for arranging/uploading; needs clear **handles** and **large drop zones**.
    
- **Swipe** for dismiss/Archive; must provide **Undo**.
    
- **Type** for precise input; support **autocomplete** and **inline validation**.
    

**Design tactics**

- Make the **primary action** a **familiar type** (tap/click).
    
- Provide **micro-feedback within ~100–200 ms** for every type (pressed state, ripple, tiny vibration).
    
- Use adequate **target sizes**, spacing from destructive buttons, and generous **drop zones**.
    
- Gestures/shortcuts are **accelerators**, not the **only** path.
    

**10-second test**

- At a glance, can you spot **what’s tappable/draggable**? If not, add signifiers (handles, borders, labels).
    

---

## One-line contrast (when you’re unsure)

- **Mode** changes the **meaning** of the same action.
    
- **Modality** changes the **channel** used to communicate.
    
- **Type** changes the **form of the action** within a channel.
    

---

## Three mini-scenarios (all three concepts at once)

**A) Camera app**

- **Mode**: Photo ↔ Video (UI and timer strip change).
    
- **Modality**: touch to trigger; optional **shutter sound** (audio) + **tiny vibration** (haptic).
    
- **Type**: tap to capture; **press-and-hold** to record; **swipe** to switch lenses.
    

**B) Navigation map**

- **Mode**: Browse (drag pans) ↔ Measure (drag draws a path).
    
- **Modality**: **voice** to enter destination; **visual** route; **haptic** buzz when GPS lock completes.
    
- **Type**: pinch to zoom; drag to adjust waypoints; tap to pick a route.
    

**C) File upload (web)**

- **Mode**: _Select_ while choosing files; _Idle_ after selection.
    
- **Modality**: **drag & drop** (visual/touch) + completion **toast** (visual) + **short tone** (audio).
    
- **Type**: drag & drop, click “Upload”, type a note.