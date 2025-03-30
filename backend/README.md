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
  "response": "I was in the library, reading ancient texts.",
  "questions_remaining": 4
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
      "role": "user",
      "parts": [
        {"text": "Where were you last night?"}
      ]
    },
    {
      "role": "model",
      "parts": [
        {"text": "I was painting in my studio."}
      ]
    }
  ],
  "questions_remaining": 3
}
```

---
