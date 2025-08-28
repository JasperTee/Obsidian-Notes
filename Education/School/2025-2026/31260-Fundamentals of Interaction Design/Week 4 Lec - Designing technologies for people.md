## Cognition
### 1) What cognition is and why it matters

- **Cognition**: how people **take in → understand → hold in mind → decide → act**.
    
- **Design meaning**: if an interface makes users **guess**, **remember a lot**, **read long text**, or **can’t see state clearly**, cognitive load rises → more errors and drop-offs.
    

---

### 2) The cognitive work your UI must support

- **Attention & Working Memory**
    
    - People can hold only **about 3–5 “chunks”** at once.
        
    - Design:
        
        - Split flows into **small steps**; show info **at the right place/time** (inline hints).
            
        - Use **autocomplete**, **recents**, **sensible defaults** to reduce typing/remembering.
            
        - Keep **one primary focus** on a screen (one clear CTA); make everything else quieter.
            
- **Comprehension**
    
    - Turn data into **meaning** quickly.
        
    - Design:
        
        - Strong **visual hierarchy**: title → subtitle → body.
            
        - **Tables/charts** for comparisons; **consistent units and number formats**.
            
        - **Plain, concise language**; avoid insider jargon.
            
- **Language (reading/writing)**
    
    - Words drive understanding and action.
        
    - Design:
        
        - **Short, specific microcopy** with **action verbs** (“Pay”, “Send”).
            
        - **Labels close to inputs**, format examples (MM/YY), helpful placeholders.
            
        - **Validation** that states the error and **how to fix it**.
            
- **Reasoning & Decision-making**
    
    - Compare, estimate, choose.
        
    - Design:
        
        - **Reduce upfront choices**, reveal advanced ones (**progressive disclosure**).
            
        - Provide **defaults** based on past behavior; **easy to change** with a short explanation.
            
        - Show **option summaries** (price, delivery time, fees) to speed decisions.
            

---

### 3) Cognitive load — three types & how to handle them

- **Intrinsic load** (inherent difficulty of the task)
    
    - You can’t remove it; you can **restructure** it.
        
    - Moves: stepwise flow; examples; **presets/smart defaults**; sample-filled forms.
        
- **Extraneous load** (burden caused by the UI)
    
    - **Eliminate** it.
        
    - Moves: clean layout; whitespace; **group related items**; avoid decorative noise; exactly **one prominent CTA**.
        
- **Germane load** (useful effort that builds understanding)
    
    - **Encourage at the right time**.
        
    - Moves: short tooltips; A/B comparisons; on-the-spot illustrations; “pro tips” after the basic step is done.
        

---

### 4) Attention & preattentive cues

- The brain detects **size, weight, position, borders, motion, direction** very fast.
    
- Design:
    
    - Create **one focal action**; make key numbers **large/bold**.
        
    - Use **panels/borders** and spacing so users “see what belongs together.”
        
    - Avoid **multiple competing highlights**.
        

---

### 5) Memory: recognition beats recall

- **Recognition > Recall**: picking from suggestions is easier than remembering.
    
- Design:
    
    - **Autocomplete**, **date pickers**, **recent addresses**, “recently used” lists.
        
    - **Preview** before commit; **labels right by fields** so users don’t need to remember “what goes here.”
        
- **Chunking**
    
    - Group elements into **meaningful chunks**.
        
    - Design: sections like **Shipping / Payment** with **clear subheadings**; split long forms into subsections.
        

---

### 6) Feedback & timing

- Every action should trigger **visible feedback within 100–200 ms** (pressed state, ripple).
    
- Tasks **> 2–3 seconds**: show a **progress bar + time estimate**; offer **Cancel** when appropriate.
    
- For important events, use **at least two channels** (icon + text; sound + banner; haptic + toast) so feedback isn’t missed.
    

---

### 7) Human errors: Slip vs. Mistake (and how to prevent)

- **Slip** (right goal, wrong action)
    
    - Solutions: **large enough targets**, separate destructive controls, **Undo** (better than constant confirms); confirm only for truly destructive actions.
        
- **Mistake** (wrong goal/rule)
    
    - Solutions: **plain language**, **feedforward** (“Press ‘Cancel’ to stop the transaction”), examples, validation that explains **how to fix**.
        

---

### 8) Patterns to use

- Task-based grouping; clear hierarchy; **ample whitespace**.
    
- **Inline hints & inline validation**; format examples at the point of input.
    
- Explicit states: **skeleton → progress → result**; short text + small icon; brief animations only.
    
- **Smart defaults** (remember addresses, payment methods); easy to override.
    
- **Undo > Are you sure?**; **progressive disclosure** for advanced options.
    

**Anti-patterns**

- Forcing users to **remember codes/IDs** across screens.
    
- **Multiple loud CTAs** at once.
    
- Long paragraphs for tiny state changes; **color-only** signals; **single-channel** feedback in risky contexts.
    

---

### 9) Quick application examples

- **Sign-up form**
    
    - Before: six equally spaced fields, two loud buttons, errors at the top.
        
    - After:
        
        - Group **Personal info** (Name, Email) and **Security** (Password, Confirm).
            
        - **Labels right next** to inputs; errors **right below** the field.
            
        - **One** prominent “Create account” button; “Learn more” becomes a quiet link.
            
        - On submit: **progress** → “Success” + code; brief **Undo** window.
            
- **Checkout**
    
    - Group as **Card / Billing / Shipping**; hints **MM/YY**, **CVV**; **instant** validation.
        
    - Single “Pay” button; after tap: progress + ETA; result page shows **summary** and **Undo** if feasible.
        
- **Search & filter**
    
    - Search with **autocomplete** (history + suggestions).
        
    - Filters as **chips** with labels; on apply → short animation + message “Filtering: size M, < 500k”.
# Perception & the Interaction Loop

**Human side**

- Perceptual channels: vision, hearing, touch.
    
- Effectors: hands/fingers (tap, type, drag), voice, body movement.
    

**System side**

- Inputs: keyboard, touch, microphone, camera, sensors.
    
- Outputs: screen, sound, vibration, lights.
    

**The loop**

- The user sees/hears/feels → forms an intention → acts → the system senses → processes → responds → the user perceives the response.
    

**Timing rule**

- Every action should receive feedback within ~100–200 ms; long tasks need a progress indicator + time estimate + a cancel option.
## Visual Perception
### Gestalt Laws

#### 1) Concept & context

- **Gestalt**: the visual system tends to organize separate elements into **meaningful wholes** (a unified configuration).
    
- Roots: German Gestalt psychology (Wertheimer, Köhler, Koffka).
    
- Implication: observers perceive **overall structure before details** (global precedence).
    
#### 2) The principles
 **1) Proximity (Grouping by nearness)**  
Content: Items placed close together are perceived as belonging to the same group.  
Example: On a supermarket shelf, noodle packs set close to one another are seen as a single “noodle section,” even without a sign.

**2) Common Region (Shared enclosure)**  
Content: Items that sit within the same tray/box/frame are perceived as one group.  
Example: Pens, a ruler, and an eraser kept in one pen tray are read as “one stationery set.”

**3) Uniform Connectedness (Consistent connection)**  
Content: Objects that are tied/stapled/attached on the same surface are strongly perceived as belonging together.  
Example: Several sheets stapled together are taken as one packet—stronger than just placing them near each other.

**4) Similarity (Look-alike → same kind)**  
Content: Things that are alike (color, style, size, etc.) are perceived as the same category.  
Example: A group of people wearing uniforms is immediately recognized as one team.

**5) Continuation / Parallelism (Smooth path / parallel rows)**  
Content: The eye prefers continuous lines and parallel arrangements; we naturally connect points into a smooth flow.  
Example: When viewing traffic in parallel lanes, your eyes smoothly scan along each lane.

**6) Figure/Ground (Figure vs. background)**  
Content: Perception separates the focus (figure) from the rest (ground). Clearer boundaries make recognition easier.  
Example: In a portrait with a blurred background, the face stands out as the figure; the scene behind recedes as the ground.

**7) Focal Point (Primary attractor)**  
Content: The most prominent element (larger/bolder/higher contrast) draws attention first.  
Example: In a slightly dark room, a bright desk lamp grabs your gaze before anything else.

**8) Prägnanz / Simplicity (Preference for the simple)**  
Content: When multiple interpretations are possible, the mind prefers the simple, stable one.  
Example: On a cluttered notice board, you grasp a few main groups (big headings) and ignore fussy details.

**9) Closure (Completing the missing parts)**  
Content: When a part is missing, the mind tends to “fill it in” to see a complete whole.  
Example: You still read “H_llo” as “Hello”; a logo partly covered is still recognized as its brand.

**10) Symmetry & Order (Balance and regularity)**  
Content: Balanced, orderly layouts are perceived more easily and as more trustworthy.  
Example: A dining table set symmetrically (two bowls and two pairs of chopsticks balanced on both sides) feels tidy and “proper.”
