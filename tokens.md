## What is a token?

A token is a basic unit of text that a model processes.

### Definition:

- Word: A word is a meaningful linguistic unit (e.g., "cat", "running", "happily").
- Token: A token is a chunk of text as broken down by the model's tokenizer, which could be a word, part of a word, or even a punctuation mark.

So, in summary

- A word is a complete linguistic unit.
- A token is how the LLM represents text, which can be a word, subword, or symbol.

### Why Tokens ≠ Words?

#### Handling Large Vocabularies Efficiently

If every word were a token, the model’s vocabulary would need to include every possible word (including misspellings, rare terms, and combinations), leading to an unmanageably large (and wasteful) vocabulary. Subword tokenization (used in models like GPT, BERT) breaks words into smaller, reusable units, for example: "Unhappiness" → ["Un", "happiness"] (reuses "happiness"). This reduces vocabulary size while maintaining coverage.

#### Managing Rare or Unknown Words

A word-based model would fail on rare words (e.g., medical terms like "Pneumonoultramicroscopicsilicovolcanoconiosis").Rare words are split into known subword tokens: for example, the above word might tokenize as ["Pneumono", "ultra", "micro", "scopic", "silico", "volcano", "coniosis"]. The model can then infer meaning from familiar pieces.

#### Consistency Across Related Words

Tokens often preserve roots, helping models generalize:

- "Running," "runs," "ran" → Share the token "run" + suffixes ("ing", "s", etc.).
- This reduces redundancy and improves learning efficiency.

#### Punctuation, Spaces, and Special Characters

Treating punctuation as separate tokens avoids ambiguity:

- "Let's eat, Grandma!" → Tokens: ["Let", "'", "s", "eat", ",", "Grandma", "!"].
- Without tokenizing punctuation, the model might misinterpret "Let's" as one unit.

#### Computational Efficiency

- Fixed Vocabulary: Models pre-define a token vocabulary (e.g., 50K–100K tokens for GPT), balancing memory and performance.
- Variable-Length Words: Tokenizing "antidisestablishmentarianism" into ["anti", "dis", "establish", ...] is cheaper than treating it as one giant, rare word.

### Summary:

Tokens are a compression mechanism for text, allowing LLMs to:

- Represent infinite possible words with a finite vocabulary.
- Generalize across languages and morphological variants.
- Process text computationally efficiently.

### References

https://platform.openai.com/tokenizer

A helpful rule of thumb is that one token generally corresponds to ~4 characters of text for common English text. This translates to roughly ¾ of a word (so 100 tokens ~= 75 words).