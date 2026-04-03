# pt-en-prompt

A Claude Code skill that translates colloquial Brazilian Portuguese messages into highly structured English prompts. 

Brazilian Portuguese prompts are often context-heavy and colloquial, whereas English prompts for AI agents require explicit requirements, scope, and constraints. This skill automatically bridges that gap, ensuring Claude understands exactly what you need.

## Features

* **Intent Extraction**: Identifies the core ask behind colloquial phrases (e.g., *"ta lento"* -> *"improve render performance"*).
* **Urgency Preservation**: Maps cultural signals like *"pra ontem"* to explicit English deadlines or urgency flags.
* **Ambiguity Resolution**: Automatically identifies vague terms and ensures they are clarified.
* **Structured Output**: Formats the final English prompt into a clean, actionable structure: `Purpose → Requirements → Constraints → Expected Deliverable → Edge Cases`.

## Installation

You can install this skill directly into Claude Code using the following command:

```bash
claude skill add https://github.com/gpaiva00/pt-en-prompt
```

Or:
```bash
# bun
bunx skills add https://github.com/gpaiva00/pt-en-prompt

# npm
npx skills add https://github.com/gpaiva00/pt-en-prompt
```

## Usage

Simply type your request in Brazilian Portuguese within Claude Code. If the message contains colloquialisms, implicit requirements, or high urgency, the skill will kick in, process the request, and output a structured English prompt in a code block.

Claude will wait for your confirmation on the structured prompt before executing the actual task.

**Example Input:**
> "me ajude a implementar tags nas tarefas, precisa funcionar offline, usar localStorage, cores customizáveis, máximo 12 cores, pra ontem"

**Example Skill Output:**
```markdown
Implement a tag system for tasks with:

**Purpose:** Categorize tasks with persistent tags across offline/online states

**Requirements:**
- Create Tag interface with id, name, color
- Assign tags to tasks
- Color picker: 12 predefined swatches
- All data persists to localStorage
- Offline-first: changes sync when connection restored

**Constraints:**
- Max 12 colors per tag system
- localStorage as data source (no API calls)
- [URGENT] Needed ASAP

**Edge Cases:**
- What happens when colors conflict with theme?
- Can users delete tags if tasks reference them?

**Expected Deliverable:** Tag interface, storage adapter, UI component
```
