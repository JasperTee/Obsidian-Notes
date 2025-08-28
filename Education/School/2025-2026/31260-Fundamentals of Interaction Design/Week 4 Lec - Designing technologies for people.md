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
## Perception & the Interaction Loop

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
### Visual Perception
#### Gestalt Laws

##### 1) Concept & context

- **Gestalt**: the visual system tends to organize separate elements into **meaningful wholes** (a unified configuration).
    
- Roots: German Gestalt psychology (Wertheimer, Köhler, Koffka).
    
- Implication: observers perceive **overall structure before details** (global precedence).
    
##### 2) The principles
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
#### Metaphors
##### 1) What is a metaphor? 

- **Metaphor** = borrowing something **familiar from real life** to **name/explain** something **new in a digital product**.
    
- **Source domain**: what you already know in the real world. **Target domain**: the function in an app/website. **Mapping**: how meanings are matched between the two.
    
- Goal: you **see it and instantly infer** what it does, **without much learning**.
    

---

##### 2) How does a metaphor work? 

- Identify the **source domain** → pick a widely known object/idea (shopping cart, trash bin…).
    
- State the **target domain** → the corresponding digital action (shopping, delete…).
    
- Make the **mapping** explicit → “cart” = collect before paying; “trash” = delete but can be restored.
    
- Ask 3 questions:
    
    1. Can a new user **guess correctly in 1 second**?
        
    2. Is the meaning **consistent everywhere** in the product?
        
    3. Are there **cultural/age mismatches** or is it outdated?
        

---

##### 3) Common metaphors 

**Trash bin → Temporary delete**  
• Meaning: move unwanted items to “trash,” with the option to **restore** before permanent deletion.  
• Implied expectation: a **Trash/Recently deleted** area and a retention period (e.g., 30 days).  
• Easy confusion: if deletion is **permanent**, users still expect “restore” → show a clear warning. 

**Shopping cart → Collect first, pay later**  
• Meaning: add items to a cart, **review**, then pay.  
• Implied expectation: **badge count** on the icon; **Save for later**; a **Review order** page.  
• Easy confusion: a **Buy now** button may **skip the cart** → label it clearly: “Buy now (skip cart)”. 

**Paperclip → Attach**  
• Meaning: attach files to an email/message.  
• Implied expectation: see the **list of attached files**, max size, allowed types.  
• Easy confusion: the paperclip can be read as “note” → add the label “Attach file”.  

**Magnifying glass → Search**  
• Meaning: open the search field and enter keywords.  
• Implied expectation: cursor **focuses** in the input; show **recent searches**.  
• Easy confusion: some apps use the magnifier for **Zoom** → add the label “Search” to distinguish.  

**Heart → Save/Like**  
• Meaning: bookmark/save or express **like**.  
• Implied expectation: if it means **Like** (social), others **see the like count**; if it means **Save**, it’s private.  
• Easy confusion: in one place it means “Like,” elsewhere it means “Save” → add a label “Like”/“Save” for consistency.  

**House → Home**  
• Meaning: go back to the **main screen/start point**.  
• Implied expectation: not “home address” or “personal page.”  
• Easy confusion: in real-estate/maps apps, the house icon may mean **home address** → add the label “Home (App)” or use a different icon for “home address.”  

**Bell → Notifications**  
• Meaning: there are **new updates**; often with a **badge count**.  
• Implied expectation: **read/unread** states; **Mark all as read**.  
• Easy confusion: bell for **mute** vs bell for **notifications** look similar → add a slashed bell for Mute.  

**Gear → Settings**  
• Meaning: **configure** options (not immediate actions).  
• Implied expectation: changes may **not apply** until Save/Apply (depending on the model).  
• Easy confusion: gear for **Admin** vs **User settings** → add a label to distinguish.  

**Star/Bookmark → Favorite/Pin**  
• Meaning: **keep** content to open quickly later.  
• Implied expectation: a place to view saved items (**Favorites/Bookmarks**).  
• Easy confusion: star = “rating” vs “save”? → add a label “Save”/“Bookmark”.  

**Ellipsis (three dots) → More options**  
• Meaning: there are **additional, lower-priority actions**.  
• Implied expectation: opens a **safe context menu**, not destructive immediately.  
• Easy confusion: users **can’t predict** what’s inside → label the menu items clearly.  

---

##### 4) When metaphors mislead 

**Ambiguous “Home”**  
• Cause: dual meaning (homepage vs home address).  
• Fix: add the label “Home,” or use a **house-with-roof + path** for homepage and a **pin/location** icon for an address.

**Outdated icon (floppy disk = Save)**  
• Cause: younger users **never used** a floppy disk.  
• Fix: add the label “Save”; or use a **cloud with up arrow** (save to cloud) if it matches the context.

**Rocket icon is vague**  
• Cause: no universal mapping (launch? boost? pro plan?).  
• Fix: add a clear label “Launch”, “Boost”, or replace with a more familiar metaphor.

**Cloud vs Wi-Fi**  
• Cause: icons look **similar**.  
• Fix: add **up/down arrows** with the cloud for upload/download; use the **fan-shaped signal** for Wi-Fi (no cloud); add labels.
### Auditory Perception 

#### What it is

- Hearing (auditory perception) is sensing **changes in air pressure over time** (sound waves) with an organ like the ear; the brain then interprets this as sound. 
    

#### Core facts you need

- **Human hearing range:** about **20 Hz–20 kHz**; the **highest piano note** is ~**4 kHz** (well within that range). 
    
- **Three basic properties of a sound wave:**
    
    - **Amplitude → perceived as volume** (loudness). 
        
    - **Frequency → perceived as pitch** (high vs low). 
        
    - **Duration → how long the sound lasts.**
        

#### Where audio appears in interactive products 

- **Ambience**, **sound effects**, **auditory feedback**, **music**, **speech/voice**. Think: background atmosphere, event pings, action confirmations, mood/brand, spoken guidance. 
---

#### Why it matters in interaction

- **Part of the human–system loop.** Systems present outcomes through “displays” that include **sound**; people sense those outcomes through channels like **vision, hearing, touch**. Interaction Design focuses mainly on **visual, audible, tactile** channels. 
    
- **Visibility of system status (faster feedback).** Audio confirms “received/processing/done” even when eyes are not on the screen (e.g., a short tone after pressing). 
    
- **Recognition over recall.** If each type of event has a familiar sound, users **recognize** it instantly instead of **remembering** rules. 
    
- **Error prevention and handling.** Alerts can stop a risky action or make users pause to confirm; clear error sounds + messages help diagnose and recover. 
    
- **Multimodal fit (context).** When hands/eyes are busy, or environments are noisy/quiet, audio is a practical channel; your course highlights choosing **modalities** (e.g., speech, touch, voice) based on context. 
    

---

#### When to use audio 

- **Auditory feedback:** confirm actions or states (“sent,” “saved,” “error”). 
    
- **Sound effects:** mark events (message arrived, toggle on/off). 
    
- **Speech/voice:** speak instructions/status when eyes or hands are occupied. 
    
- **Music/ambience:** set atmosphere and pace (used sparingly). 
    

#### Practical principles 

- **Clear & timely:** sounds should quickly reveal system status. 
    
- **Consistent mapping:** the same kind of event → the same kind of sound. 
    
- **Minimal, not noisy:** use only what helps the task now (aesthetic & minimalist). 
    
- **User control:** let users toggle sounds, set volume, or mute (flexibility & efficiency). 
    
- **Helpful errors:** pair error sounds with plain-language fixes (recognize/diagnose/recover). 
    

---