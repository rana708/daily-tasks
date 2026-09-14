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



**Case 3: Flutter Widget/Property Hallucination (Inventing non-existent properties or widgets)**

**Scenario:**

When asking the model how to add a bouncing scroll effect inside a `ListView`, it might suggest a property that does not exist in the widget's API.

**Example:**

```dart
// Incorrect answer:
ListView(
  bounceEffect: true, // Non-existent property in Flutter
  children: [...],
)

```

There is no property named `bounceEffect` in `ListView`. The correct way to configure this behavior is by setting `physics: BouncingScrollPhysics()`.

**Root Cause:**

* The model infers parameter names based on the literal semantic description of the requested feature ("bounce effect") rather than referencing Flutter's actual API signatures.
* The large volume of similar configuration properties across various Flutter widgets (e.g., `physics`, `scrollDirection`, `shrinkWrap`) increases the chance of generating an intuitively named but completely fake property.

**Proof:**

The official Flutter API reference (`api.flutter.dev`) for the `ListView` class lists no parameter named `bounceEffect`. The only property that controls scrolling behavior dynamics is `physics`.



**Case 4: MySQL Function Hallucination (Inventing non-existent SQL functions)**

**Scenario:**

When asking the model how to calculate the difference between two dates in months using MySQL, it might suggest a function that does not exist in the MySQL database engine.

**Example:**

```sql
-- Incorrect answer:
SELECT MONTHS_BETWEEN(end_date, start_date) FROM orders;

```

The function `MONTHS_BETWEEN()` exists in Oracle DB, but it is not available in MySQL. The correct approach in MySQL is using `TIMESTAMPDIFF(MONTH, start_date, end_date)` or `PERIOD_DIFF()`.

**Root Cause:**

* The model was trained on code and documentation across multiple database engines (Oracle, PostgreSQL, MySQL, SQL Server) and cross-contaminates functions that serve similar purposes across different dialects.
* The shared standard SQL syntax across database systems increases the probability of leaking vendor-specific functions into the wrong SQL dialect.

**Proof:**

The official MySQL Reference Manual (`[dev.mysql.com/doc](https://dev.mysql.com/doc)`) under the "Date and Time Functions" section lists no function named `MONTHS_BETWEEN`. That specific function is documented exclusively in Oracle's SQL documentation.


**Case 5: cPanel Path or Setting Hallucination (Inventing non-existent control panel paths or tool names)**

**Scenario:**

When asking the model how to change the PHP version for a specific website in cPanel, it might give an inaccurate tool name or dashboard navigation path.

**Example:**

> "Go to **Settings > Server Configuration > PHP Engine Selector** and select your desired PHP version."

There is no tool named "PHP Engine Selector" in cPanel. The correct name of the tool is **"MultiPHP Manager"** (or **"Select PHP Version"** when using CloudLinux/CloudLinux PHP Selector), and it is located under the **Software** section, not "Server Configuration."

**Root Cause:**

* cPanel interface labels can vary slightly across software versions and web hosting providers (many hosts apply custom themes or plugins), causing the model to construct a "plausible-sounding" path rather than using exact official terminology.
* Lack of real-time interface rendering leads the model to synthesize descriptive UI labels instead of verifying the current control panel layout.

**Proof:**

The official cPanel documentation (`docs.cpanel.net`) explicitly identifies the management tools as **"MultiPHP Manager"** and **"MultiPHP INI Editor"** inside the **Software** section. There is no record of a tool named "PHP Engine Selector" in any official cPanel release.
