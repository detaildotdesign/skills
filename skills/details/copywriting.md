# Copywriting Details

Microcopy, labels, prompts, help text, errors, warnings, empty states, and human-readable next actions that make the interface easier to trust and act on.

**Skip when:** The string is a machine contract: API payloads, enum values, config keys, telemetry, logs, test fixtures, code literals, parseable output, or third-party text that must remain exact. Do not rewrite user-generated content for style.

## 1. Name the object before asking for action

Use concrete nouns for the thing being changed, created, deleted, selected, or configured. "Connect your GitHub account" tells the user which account is affected; "Connect your account" forces them to infer scope.

## 2. Keep one noun per concept

Choose the product term once and reuse it across labels, prompts, empty states, errors, and success messages. Do not alternate between "workspace", "team", and "organization" unless the product model truly has three distinct things.

## 3. Match the verb to the mutation

Use `create` for making a new resource, `add` for attaching an existing one, `remove` for detaching without destroying data, `delete` for permanent destruction, `disconnect` for integrations, and `revoke` for credentials. The confirmation and result should use the same verb.

## 4. Put the recovery step last

When something fails, state what failed, give the known cause or constraint, then end with the action the user can take next. The last line is the one people act on.

## 5. Route permission and plan denials to the resolver

Do not stop at "You don't have permission." Name who or what can resolve it: an owner, admin, login, team switch, settings page, upgrade, docs page, or support path.

## 6. Ask prompts for one concrete concept

Prompt for the smallest safe decision: "Which team?", "Project?", "Environment?", or "Name?" Avoid multi-part prompt copy and yes/no questions unless the user is confirming a previewed action.

## 7. Use status copy for current state, not promises

Loading and progress text should describe the phase that is happening now, not guarantee a result that may still fail. Pair progress with present participles and results with past-tense receipts.

## 8. Replace blame with constraints

Phrase validation around the rule the value must satisfy, not the user's mistake. The copy should teach the shape of valid input without scolding.

## 9. Make empty states actionable

An empty state should name what is absent and offer the exact next action when one exists. Avoid generic "Nothing here" copy unless there is no safe action to suggest.

## 10. Cut filler and hype

Remove words that do not change the user's action or understanding: "just", "simply", "actually", "seamlessly", "powerful", "robust", and "leverage". Plain product copy is easier to trust than promotional language in a working interface.

## 11. Write a thoughtful "What's New" message

Even a changelog few people read deserves real copy. Skip the bare "Bug fixes and improvements" — a warm, specific line acknowledges the quiet work and makes the release feel cared-for.

## 12. Use human-readable IDs

For user-visible identifiers, generate readable project-scoped IDs like `DTD-123` instead of UUIDs or raw auto-increments — they're easy to remember, say aloud, and reference in conversation. For IDs users never see, like a database index, random strings are fine.

## 13. Tailor CTA copy to the visitor's time

Phrase the call to action against the current moment — "Start Building Tonight," "Try Better Reading This Weekend," "Send a Gift by Christmas." The same button feels written for this visitor, right now.

## 14. Pluralize labels to match the count

"1 items" reads as a bug. Switch the noun on the count so singular and plural always agree, treating microcopy as a first-class detail.
