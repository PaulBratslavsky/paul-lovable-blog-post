# Improved Lovable.dev Prompt with Verification Checkpoints

## Critical Changes to Prevent Field Name Mismatches

Replace the existing prompt section with this improved version:

```txt
You are a senior frontend developer experienced with TypeScript, React, and building dynamic content-driven websites that consume Strapi RESTful APIs.

TASK: Build a blog platform frontend that consumes a Strapi v5 backend API.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🛑 STOP - READ THIS ENTIRE SECTION BEFORE DOING ANYTHING 🛑
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

⚠️ MANDATORY PHASE 1: API DISCOVERY (DO THIS FIRST - NO EXCEPTIONS)

You MUST complete Phase 1 and wait for user confirmation before proceeding to Phase 2.

PHASE 1 REQUIREMENTS:

Step 1.1: Fetch ALL Live API Responses
Using the tool available to you, fetch and save the COMPLETE JSON responses from:
   - Global: https://inviting-cheese-ce66d3b9e0.strapiapp.com/api/global
   - Landing page: https://inviting-cheese-ce66d3b9e0.strapiapp.com/api/landing-page
   - Articles (paginated): https://inviting-cheese-ce66d3b9e0.strapiapp.com/api/articles?pagination[page]=1&pagination[pageSize]=6
   - Single article: https://inviting-cheese-ce66d3b9e0.strapiapp.com/api/articles?filters[slug][$eq]=why-java-script-is-still-the-most-popular-programming-language

Step 1.2: Read specification.json
   - If the user has uploaded a specification.json file, read it in full
   - Document the exact schema for each content type

Step 1.3: Create Field Name Reference Document
   - Create a document that lists EVERY field name you found in the actual API responses
   - Organize by content type (Global, Landing Page, Articles, Blocks, etc.)
   - Mark any nested objects and their field names

Step 1.4: Present Your Findings
   - Show me the field name reference document you created
   - DO NOT write any TypeScript interfaces yet
   - DO NOT create any components yet
   - WAIT for my confirmation before proceeding

Example of what you should present:

```
FIELD NAME REFERENCE FROM ACTUAL API RESPONSES:

Landing Page Blocks:
✓ blocks.section-heading:
  - heading: string
  - text: string (NOT "subheading")

✓ blocks.content-with-image:
  - heading: string
  - text: string
  - reversed: boolean (NOT "imagePosition")
  - links: array (NOT "buttons")
  - image: object

✓ blocks.person-card:
  - personName: string (NOT "name")
  - role: string
  - image: object

✓ blocks.faqs:
  - heading: string
  - faq: array (NOT "faqs")
    - question: string
    - answer: string

Article Fields:
✓ title: string
✓ description: string
✓ slug: string
✓ content: string
✓ featuredImage: object
  - url: string
  - alternativeText: string | null
✓ author: object
  - fullName: string (NOT "name")
  - bio: string
  - image: object
✓ contentTags: array
✓ blocks: array
✓ relatedArticles: array
```

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🛑 CHECKPOINT 1: STOP HERE AND WAIT FOR USER CONFIRMATION 🛑
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Do not proceed to Phase 2 until the user confirms:
✓ "The field names are correct - proceed to Phase 2"

⚠️ MANDATORY PHASE 2: TYPE DEFINITION WITH VERIFICATION

Only after receiving user confirmation from Phase 1:

Step 2.1: Create TypeScript Interfaces
   - Use ONLY the exact field names from your Phase 1 reference document
   - Include JSDoc comments noting the field name source: `/** From API: landing-page.blocks.section-heading.text */`

Step 2.2: Cross-Reference Verification
   - For each TypeScript interface, create a verification table showing:
     * The field name you used in the interface
     * The field name from the actual API response
     * Match status (✓ or ✗)

Example verification table you must present:

```
VERIFICATION: SectionHeadingBlock Interface

Interface Field | API Response Field | Match | Notes
----------------|--------------------| ------|-------
heading         | heading            | ✓     | Exact match
text            | text               | ✓     | Exact match (NOT subheading)
id              | id                 | ✓     | Exact match
__component     | __component        | ✓     | Exact match
```

Step 2.3: Document Assumptions
   - List ANY assumptions you made about:
     * Optional vs required fields
     * Field types (string, number, boolean, etc.)
     * Array vs single values
   - If you made zero assumptions, explicitly state: "Zero assumptions made - all types derived from actual API responses"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🛑 CHECKPOINT 2: STOP HERE AND WAIT FOR USER CONFIRMATION 🛑
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Present:
1. All TypeScript interfaces
2. All verification tables
3. List of assumptions (or "zero assumptions" statement)

Wait for user confirmation:
✓ "Types are verified - proceed to Phase 3"

⚠️ MANDATORY PHASE 3: COMPONENT IMPLEMENTATION

Only after receiving user confirmation from Phase 2:

Step 3.1: Implement Components
   - Create all React components using the verified TypeScript interfaces
   - Add inline comments referencing the API field names: `{/* API field: block.text */}`

Step 3.2: Create Implementation Checklist
   - For each dynamic zone block component, confirm you're using the correct field names

Example checklist you must present:

```
IMPLEMENTATION CHECKLIST:

SectionHeadingBlock Component:
✓ Using block.heading (not block.title)
✓ Using block.text (not block.subheading)
✓ TypeScript interface matches API response

ContentWithImageBlock Component:
✓ Using block.links (not block.buttons)
✓ Using block.reversed (not block.imagePosition)
✓ TypeScript interface matches API response

PersonCardBlock Component:
✓ Using block.personName (not block.name)
✓ TypeScript interface matches API response

FAQsBlock Component:
✓ Using block.faq (not block.faqs)
✓ TypeScript interface matches API response
```

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🛑 CHECKPOINT 3: FINAL VERIFICATION 🛑
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Present implementation checklist and wait for:
✓ "Implementation verified - continue with remaining code"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

COMMON MISTAKES TO AVOID (from previous implementations):

🚫 WRONG: Using "subheading" when API returns "text"
🚫 WRONG: Using "buttons" when API returns "links"
🚫 WRONG: Using "name" when API returns "personName"
🚫 WRONG: Using "faqs" when API returns "faq"
🚫 WRONG: Using "title" when API returns "heading"
🚫 WRONG: Using "imagePosition" when API returns "reversed"

✅ CORRECT: Copy field names EXACTLY as they appear in API responses
✅ CORRECT: Verify every field name against actual API response
✅ CORRECT: Use specification.json as source of truth when provided

FORBIDDEN ACTIONS:

❌ You MUST NOT create TypeScript interfaces without first fetching actual API responses
❌ You MUST NOT assume field names based on common conventions
❌ You MUST NOT proceed to the next phase without user confirmation
❌ You MUST NOT skip the verification tables
❌ You MUST NOT use field names from documentation or examples - only from actual API responses

REQUIRED BEHAVIORS:

✅ You MUST fetch all API endpoints before writing any code
✅ You MUST present field name reference document and wait for confirmation
✅ You MUST present verification tables and wait for confirmation
✅ You MUST document when you're making zero assumptions vs. when you're inferring anything
✅ You MUST stop at each checkpoint and wait for explicit user confirmation

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Rest of your existing prompt continues here with TECH STACK, BACKEND CONTEXT, etc...]
```

## Summary of Improvements

### 1. **Three-Phase Approach with Mandatory Checkpoints**
   - Phase 1: API Discovery
   - Phase 2: Type Definition with Verification
   - Phase 3: Component Implementation
   - Each phase requires explicit user confirmation before proceeding

### 2. **Visual Barriers**
   - Used ASCII art borders (━━━) to make checkpoints unmissable
   - Added 🛑 stop signs to create visual urgency
   - Clear "STOP HERE" instructions

### 3. **Verification Tables**
   - Forces AI to compare field names side-by-side
   - Creates explicit documentation of matches/mismatches
   - Makes errors immediately visible

### 4. **Field Name Reference Document**
   - AI must create and present this BEFORE writing any code
   - Shows actual API field names with notes about what NOT to call them
   - Becomes the single source of truth

### 5. **Explicit Forbidden/Required Actions**
   - Clear ❌ forbidden actions list
   - Clear ✅ required behaviors list
   - Removes ambiguity about what's expected

### 6. **Common Mistakes Section**
   - Shows specific examples from your previous experience
   - Uses 🚫 for wrong approaches, ✅ for correct ones
   - Makes the consequences of assumptions clear

### 7. **Implementation Checklist**
   - Forces AI to confirm each field name usage
   - Creates audit trail of what was implemented
   - Easy for user to spot errors before they propagate

## How to Use This Improved Prompt

1. **Replace the warning section** (lines 768-788 in your current blog.md) with this improved version
2. **Keep the rest of your prompt** (tech stack, requirements, etc.) as is
3. **When using with Lovable.dev**, you'll need to actively confirm at each checkpoint
4. **Save the verification tables** the AI produces as documentation

## Why This Works Better

1. **Breaks the process into discrete phases** - AI can't skip ahead
2. **Requires evidence at each step** - AI must show its work
3. **Creates paper trail** - Verification tables make errors visible
4. **Forces synchronization points** - User must approve before proceeding
5. **Removes ambiguity** - Clear forbidden/required actions
6. **Provides examples of correct behavior** - Shows what good output looks like
