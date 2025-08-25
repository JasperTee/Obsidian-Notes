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