# Data

The anonymised tables every analysis in the paper runs on. Five CSVs, plus
`data_all_tables.xlsx`, which holds the same five as one sheet each for readers who prefer Excel.
The CSVs are the authoritative copies; the workbook is a convenience.

## Anonymisation

**Participant identifiers were replaced.** The working tables carried Qualtrics response IDs.
Those are pseudonyms rather than anonymous data — they key back to rows in the original export —
so each was replaced by a sequential code, `P001` to `P170`. The mapping is held privately by the
authors and is not part of this package. Network numbers and role letters are kept, because the
analyses need them; someone who already held the original export could therefore re-link the two,
but nothing in this package identifies a person on its own.


## The tables

| file | what one row is |
|---|---|---|
| `participants.csv` | one participant, with their network and how much they recalled before and after |
| `conversations.csv` | one conversation, with its network, dyad, round, length, and whether it was analysed |
| `conversation_turns.csv` | one turn in one conversation, in order, with what was typed and how it was classified |
| `individual_recall.csv` | one production in one individual recall, in output order |
| `stimuli.csv` | one studied word or lure, with the list it belongs to |

250 of the 255 conversations were analysed. The five excluded are marked in `conversations.csv`,
and their turns are not in `conversation_turns.csv`. In two networks some participants entered
several words in one turn, and the analyses require one word per turn so that adjacent turns can be
compared; a conversation was excluded when a quarter or more of its turns were such lists.

## Columns that carry the classification

`kind` appears in both recall tables and takes four values. `studied` is one of the hundred
presented words. `lure` is one of the ten never-presented words each list converges on; it carries
its list's category and therefore continues a run. `other` is a word belonging to no list, which
ends a run. `pass` is the pass token, available in conversation only, which also ends a run.

`list` and `item_id` identify the category and the word. `list` is filled for `studied` and `lure`
productions and empty for the rest. `item_id` identifies the studied word for `studied`
productions; in `individual_recall.csv` a lure carries the original file's lure number (101-110),
and in `conversation_turns.csv` it carries none. A participant's store counts studied words only.

**Spelling variants.** A misspelling, plural or related form of a studied word ("diamante" for
"diamantes", "volar" for "vuelo") does not match the stimulus exactly, but the original scorers
coded it correct and gave it the item number. Such productions are counted as that studied word in
individual recall. The forms the scorers accepted are applied in the same way to the conversation
transcripts, which carry no scoring of their own. A pass typed in quotation marks counts as a pass.

`variant` (in `individual_recall.csv`) is 1 for a production the original scorers accepted as a
variant form of a studied word or of a lure, and 0 otherwise.

## Every column

**participants.csv** — `participant` (P001–P170); `network` (1–17); `role` (the participant's
letter within their ten-person network, A–J); `topology` (clustered or non-clustered, the network
structure of the original study, not analysed here); `n_pre`, `n_post` (number of studied-word
productions in the first and second individual recall, repeats included); `conversations_included`
(how many of the participant's conversations were analysed, 1–3).

**conversations.csv** — `conversation` (network and the two role letters, e.g. `16_HJ`);
`network`; `dyad` (the two role letters); `topology`; `round` (the conversation slot, 1–4, in
which it was held); `n_turns` (turns in the conversation); `n_list_turns` (turns in which several
words were entered at once); `included` (whether it was analysed).

**conversation_turns.csv** — `conversation`, `network`, `dyad`, `topology`, `round` as above;
`turn_index` (position of the turn in the conversation, from 0); `speaker_role` (the writer's role
letter); `participant` (the writer); `nth_conversation_for_speaker` (whether this was the writer's
first, second or third conversation); `text` (what was typed); `kind`, `item_id`, `list` (see
above).

**individual_recall.csv** — `participant`; `phase` (`pre` for the first individual recall, `post`
for the second); `output_position` (order of the production within that recall, from 0);
`item_id`, `word`, `list`, `kind`, `variant` (see above).

**stimuli.csv** — `item_id`; `word`; `list` (1–10); `is_lure` (True for the ten never-presented
words).
