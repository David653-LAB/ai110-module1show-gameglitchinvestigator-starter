# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?

It looked normal at first but you can spot quite a few bugs.
- 
List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").
  The first error was the attempts being incorrect and the game being unable to reset.

  

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| 70    |game should reset  |game doesnt reset| start new game which|
||hard mode| large sample size| 1-50 is too easy| far too easy!
|attempts| should display correct # | wrong amount of attempts| |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?

Mainly used Claude Code.

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result) 

attempt_limit_map = {
    "Easy": 6,
    "Normal": 9,
    "Hard": 10,   hard mode was changed to 200 but since 5 attempts is too unfair it was bumped to 10 which It was only done since it was simple fix.

- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.

if st.session_state.get("difficulty") != difficulty:
    st.session_state.difficulty = difficulty
    st.session_state.secret = random.randint(low, high)
    st.session_state.attempts = 0
    st.session_state.score = 0
    st.session_state.history = []
    st.session_state.status = "playing"

this was supposed to fix the secret but it was too bloated and it feel too messy for a small error so it suggested this line if "secret" not in st.session_state or not (low <= st.session_state.secret <= high):
    st.session_state.secret = random.randint(low, high)


---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?

If the bug isn't pressent it was a success. 

- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.

The test I ran is resetting the game, as in when you press new game you had to reload it insttead of a new game started but once the code was modified I was able to reset the game without loading.

- Did AI help you design or understand any tests? How?

showed me that what was the issue which was st.session_state.status = "playing" which really made it so it wouldn't reset but AI suggested to add  st.session_state.attempts = 0
    st.session_state.score = 0
    st.session_state.history = []
    st.session_state.status = "playing"
    st.session_state.secret = random.randint(low, high) mainly low and high to replace the numbers and it worked flawlessly.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

Streamlit is like a way for python to open up an application or tab onto your browser! It is pretty cool never seen it before so it is quite a handful but I know you will have fun with it.

--- 

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.

  Ask questions, a lot you have an AI tool so do not be afraid to challenge it even if you don't think its right try to see what you can do then see what AI thinks and see why it was the case.

- What is one thing you would do differently next time you work with AI on a coding task?

I would try to ask for something more simpler so my mind can process it better but I would also say I rather just continue to challenge and learn from my mistakes.

- In one or two sentences, describe how this project changed the way you think about AI generated code.

This was my first time using Github and in general it was exhausting, stressful, and a pain but ultimately I learned AI makes mistakes and also make you type out a long winded code when I have seen examples of other programmers finding out how to make coding look more consise and less cluttered. AI generated code means we just navigate and direct the AI into what we want.