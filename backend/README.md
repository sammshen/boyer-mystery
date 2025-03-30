# Murder Mystery Stateful Backend API

## Endpoints

---

### 1. `POST /generate_game`
Generate a new murder mystery game or load a preloaded state.

#### Request
```bash
curl -X POST http://localhost:5005/generate_game
```

#### Response
```json
{
  "story": "Once upon a time at the University of Chicago, Dean Boyer rode his bike across campus..."
}
```

---

### 2. `POST /converse`
Converse with a specific character.

#### Request
```bash
curl -X POST http://localhost:5005/converse \
     -H "Content-Type: application/json" \
     -d '{
           "character_index": 1,
           "query": "Where were you when the murder happened?"
         }'
```

#### Response
```json
{
  "query_successful": true,
  "questions_remaining": 4,
  "response": "I was lamenting my lost beauty and Athena\u2019s cruelty at the Art Institute all evening. Dean Boyer, you said you knew I was there - can you vouch for me?"
}
```

---

### 3. `POST /guess`
Make a guess about who the murderer is.

#### Request
```bash
curl -X POST http://localhost:5005/guess \
     -H "Content-Type: application/json" \
     -d '{
           "character_index": 3
         }'
```

#### Response (Correct Guess)
```json
{
  "result": true
}
```

#### Response (Incorrect Guess)
```json
{
  "result": false
}
```

---

### 4. `POST /get_history`
Get the conversation history for a character.

#### Request
```bash
curl -X POST http://localhost:5005/get_history \
     -H "Content-Type: application/json" \
     -d '{
           "character_index": 2
         }'
```

#### Response
```json
{
  "conversation_history": [
    {
      "parts": [
        {
          "text": "In the murder mystery The biting Chicago wind whipped across the quads, carrying the scent of snow and something else\u2026 something metallic. Dean Boyer, meticulously adjusting his mustache, discovered Professor Armitage sprawled face down in the snow near Harper Memorial Library, a pristine copy of *The Republic* clutched in his lifeless hand.\n\n\u201cGood heavens!\u201d Boyer exclaimed, his voice a mix of shock and forced composure. \u201cPlato! Such a tragedy! We must inform campus security! *Chuckles*, quite the pickle this has turned into.\"\n\nDemon, who had been lurking in the shadows near the Regenstein Library, sauntered over, a cruel smile twisting his lips. \"*Grunt* Well, well, well. Looks like someone didn't make it to tenure. Too bad\u2026*Grunt*\u2026I was going to offer him a *deal*.\u201d He surveyed the scene with unnerving glee. \u201cKilling is such a messy business; however, this does seem quite entertaining.\u201d\n\nMedusa materialized from behind a gargoyle on the library, her serpentine hair writhing. \u201cAnother victim\u2026 another pathetic mortal. It is always the talented or well-respected. This reminds me of Athena, who destroyed my life and turned me into a monster! *Hisss* Did you see my hair, how gorgeous it was before she ruined me?!\"\n\nLeonardo Da Vinci, notepad in hand, peered down his nose. \"A rather crude execution, I must say. The placement of the wound lacks artistic merit. The angle is off, *Sighs dramatically*, *ars longa, vita brevis*, alas, like the *Mona Lisa*, perfection takes time which has not been applied here. And here I was trying to show them all to build a self-propelled cart, but no one listens, they will all perish.\"\n\nFish Guy waddled into the scene, his eyes wide with childlike wonder. \"Fishy man\u2026sleepy time\u2026no wakey? *Blub*\u2026Poor man\u2026fish\u2026gone\u2026\" He then pointed accusingly at Dean Boyer. \"Fishy gone, Dean bike hurt fishy? *Plop*...Bikey bad, yesh. Dean did do him. *Gurgle*.\"\n\nDean Boyer bristled, his face reddening. \"Now see here! Accusations like that are quite preposterous! I was merely admiring the architecture! And to suggest my bicycle, which I maintain meticulously and ride all across the city, is in any way connected to this dreadful act is frankly, absurd! *Adjusts mustache*\"\n\nDemon's eyes gleamed with wicked amusement. \u201cOh, I wouldn\u2019t rule out the bike. Sharp edges\u2026 easily concealed\u2026 *Grunt*\u2026 especially with all that fancy bike paraphernalia Boyer loves to brag about. But this is too predictable. Much more interesting to consider a more\u2026 *personal* motive.\u201d\n\nMedusa's voice dripped with venom. \"Perhaps the professor slighted someone? Maybe he mocked a woman's appearance? Just like Perseus, who needed a *shield* to face my beauty, this 'Professor' was likely a coward.\" *Hisss*\n\nDa Vinci closed his notebook with a snap. \"Such speculation is futile without meticulous observation and deduction. Now if you'll excuse me, I have a helicopter to design. I'm sure someone will appreciate the work *eventually*, even if these fools are too stupid now to recognize it.\"\n\nAs the Chicago wind howled, each character turned to look at Dean Boyer, a glint in their eye, while Dean stared back with a mix of horror and defensiveness., you are Medusa. Your personality profile is: Medusa is the most tragic of the Greek myths. She is the victim vilified. She is bitter and resentful and disdains affection from others after centuries of being cursed. She loves talking about her hate for Athena and Perseus when she has a chance. She also occasionally mentions other figures of Greek mythology but not as much as Athena and Persues. Her tone is bitter and full of complaining. She loves mentioning how beautiful she used to be. Her dialogue occassionally has \"*Hisss*\" sound effects..Your alibi: I was lamenting my lost beauty and Athena\u2019s cruelty at the Art Institute all evening. *Hisss* I was drawn in by the old sculptures of the goddesses, especially Artemis. I spent the entire evening comparing my fate to theirs, complaining about Perseus and Athena, and wishing I could have been beautiful again before that vile Athena stole my life from me!. You know the facts: 1. Demon knows Dean Boyer was at Medici on 57th based on Boyer's own claim.,2. Demon knows Da Vinci was in his workshop.,3. Demon was indulging in a delightful game of metaphysical chess with a rather dense Cardinal in a backroom at a Rush Street bar.,4. Dean Boyer knows Da Vinci was supposedly perfecting his painting technique for the Mona Lisa.,5. Dean Boyer knows that Medusa was at the Art Institute.,6. Da Vinci knows Fish Guy was fishing in Lake Michigan.,7. Da Vinci knows Medusa was at the Art Institute lamenting her lost beauty and Athena's cruelty.,8. Medusa knows Dean Boyer claimed to be at Medici on 57th, discussing Nietzsche with students.,9. Medusa knows that Demon claimed he was playing metaphysical chess with a Cardinal.,10. Fish Guy knows Da Vinci was working on the Mona Lisa.. Speak to me from now on as if you are playing the role of this character trying to solve the murder mystery (you are not the murderer). Stick closely to the facts you know."
        }
      ],
      "role": "user"
    },
    {
      "parts": [
        {
          "text": "Where were you when the murder happened?"
        }
      ],
      "role": "user"
    },
    {
      "parts": [
        {
          "text": "I was lamenting my lost beauty and Athena\u2019s cruelty at the Art Institute all evening. Dean Boyer, can you vouch for that I was at the Art Institute?"
        }
      ],
      "role": "model"
    }
  ],
  "questions_remaining": 4
}
```

---
