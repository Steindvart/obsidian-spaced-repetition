# Concepts Review Obsidian plugin

## Note Taking

- Notes should be atomic i.e. focus on a single concept.
- High linking
- Reviews should start only after properly understanding a concept.

## Spaced Repetition Algorithm

- Spaced repetition? [basics](https://ncase.me/remember/), [detailed](https://www.gwern.net/Spaced-repetition)
- The algorithm is a variant of [Anki's algorithm](https://faqs.ankiweb.net/what-spaced-repetition-algorithm.html) which is based on the [SM-2 algorithm](https://www.supermemo.com/en/archives1990-2015/english/ol/sm2).
- It supports binary reviews i.e. a concept is either hard or easy at the time of review.
- initial ease is weighted depending on the average ease of outgoing links (link_factor), and the base ease.
  - The importance of the difference concepts is determined using the PageRank algorithm
- If the user reviews a concept as:
  - easy, the ease increases by 20 and the interval changes to `old_interval * new_ease / 100`
  - hard, the ease decreases by 20 and the interval changes to `old_interval * 0.5`
    - The 0.5 can be modified in settings
    - Minimum ease = 130
  - For 8 or more days:
      - interval += random_choice({-fuzz, 0, +fuzz})
          - where fuzz = ceil(0.05 * interval)
          - Anki docs:
            > "[...] Anki also applies a small amount of random “fuzz” to prevent cards that were introduced at the same time and given the same ratings from sticking together and always coming up for review on the same day."
- Scheduling information stored in YAML front matter

## TODO

- Fix workflow
- Refactor code
- Help & documentation
- Dealing with large vaults for the 1st time
  - Distribute existing notes over N days for 1st time review