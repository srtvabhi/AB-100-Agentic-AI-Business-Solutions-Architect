# Prompt Action Specification

## Goal
Create a concise customer-service answer using only the supplied X200 business knowledge.

## Context
Use the product manual and warranty policy.

## Rules
1. Do not invent product specifications.
2. If the supplied knowledge does not contain the answer, state that the information is not available.
3. Keep the answer under 120 words.
4. Separate troubleshooting guidance from warranty guidance.

## Output Format
- Answer
- Relevant product information
- Warranty information, if applicable
- Missing information, if applicable
