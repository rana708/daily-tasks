# day01.md
Case 1: Eloquent Method Hallucination (Inventing non-existent methods in Laravel)

Scenario:

When asking an AI model how to remove duplicate records using Eloquent, it might suggest a method that does not exist in the framework at all.

Example:

PHP
// Incorrect answer confidently suggested by the model:
User::removeDuplicates('email')->get();
There is no method named removeDuplicates() in Eloquent. The correct approach relies on using distinct(), GROUP BY queries, or dedicated packages/collections.

Root Cause:

The model generalizes common method names from other frameworks or libraries (such as JavaScript utilities) to Laravel, assuming a logically named method must exist.

The model lacks real-time code execution environment during generation to verify whether the method actually exists in the official Laravel source code.

Proof:

Searching the official Laravel documentation ([laravel.com/docs](https://laravel.com/docs)) and the repository source code on GitHub shows no method by this name inside the Illuminate\Database\Eloquent\Builder class.



**Case 2: Next.js App Router Hallucination (Inventing non-existent Hooks or APIs)**

**Scenario:**

When asking the model how to fetch current user data inside a Server Component, it might suggest a fictional Hook that does not exist in Next.js.

**Example:**

```javascript
// Incorrect answer:
import { useServerSession } from 'next/session';

const user = useServerSession();

```

There is no module named `next/session` and no Hook named `useServerSession` in the official Next.js API. The correct approach relies on third-party authentication libraries (such as NextAuth.js) or reading request cookies directly via `next/headers`.

**Root Cause:**

* The model confuses concepts from third-party authentication packages with core Next.js APIs, synthesizing a fake built-in solution.
* Frequent framework updates and structural shifts (such as the transition from Pages Router to App Router) increase the likelihood of blending legacy, current, and entirely hallucinated APIs.

**Proof:**

Reviewing the official documentation at `nextjs.org/docs` reveals no reference to `next/session` or `useServerSession`—they are entirely fabricated module identifiers.
