---
name: domain-model-generate
description: Generate Domain-Driven Design (DDD) models. Defines ubiquitous language, bounded contexts, aggregates, entities, and value objects.
required_roles:
  scribe: roles/scribe.editor
personas: [software-architect, systems-analyst, product-manager]
---

# Domain Model Generate Skill

Create a Domain-Driven Design (DDD) model to structure software complexity based on the underlying business domain. This skill establishes the foundation for software architecture by mapping out the conceptual domain, defining clear boundaries, and establishing a common vocabulary.

## Inputs

- `DOMAIN_DESCRIPTION` - Detailed description of the business domain, requirements, or problem space (e.g., "E-commerce order fulfillment system" or a link to a requirements document).
- `FORMAT` - (Optional) Output format: "markdown", "mermaid", "json" (default: "markdown").
- `FOCUS_AREA` - (Optional) Specific bounded context or process to focus on if the domain is exceptionally large.

## Workflow

### Step 1: Ubiquitous Language Definition

Analyze the `DOMAIN_DESCRIPTION` to extract the common language used by domain experts.
- Identify core concepts, actions, and rules.
- Create a glossary of terms to ensure consistent communication across technical and non-technical teams.

### Step 2: Bounded Context Identification

Divide the overarching domain into distinct semantic boundaries.
- Define specific sub-domains (e.g., Billing, Shipping, Inventory).
- Clarify the context map, detailing how different bounded contexts interact and share information.

### Step 3: Structural Modeling

Within each Bounded Context, identify the building blocks:
- **Aggregates**: Clusters of domain objects that can be treated as a single unit (e.g., an Order and its Line Items).
- **Entities**: Objects defined by a thread of continuity and identity (e.g., a Customer with a unique ID).
- **Value Objects**: Objects that describe characteristics but have no conceptual identity (e.g., an Address or a Money amount).

### Step 4: Behavioral Modeling (Domain Events)

Identify significant occurrences within the domain.
- Define **Domain Events** (e.g., `OrderPlaced`, `PaymentSucceeded`) that trigger subsequent processes or inform other bounded contexts.

### Step 5: Output Generation

Synthesize the defined concepts into the requested `FORMAT`.
- Organize the output clearly, ensuring the relationship between the Ubiquitous Language, Bounded Contexts, and Structural Models is evident.

## Required Outputs

A comprehensive domain model document in the requested `FORMAT`.

**Example (Markdown excerpt):**

```markdown
# Domain Model: E-commerce Fulfillment

## Ubiquitous Language
- **Order**: A customer's request to purchase goods.
- **Fulfillment Center**: A location where inventory is stored and orders are packed.

## Bounded Contexts
### 1. Order Management Context
- **Aggregate Root**: `Order` (Entity)
  - Contains: `OrderLineItem` (Entity)
  - References: `ShippingAddress` (Value Object)
- **Domain Events**: `OrderCreated`, `OrderCancelled`

### 2. Inventory Context
- **Aggregate Root**: `ProductInventory` (Entity)
- **Domain Events**: `StockReserved`, `StockDepleted`
```

## Quick Reference

- **Purpose**: Align software design with business realities and manage complexity.
- **Key Concepts**: Ubiquitous Language, Bounded Context, Aggregate, Entity, Value Object, Domain Event.
- **When to Use**: During system design, when refactoring legacy code, or when onboarding teams to a complex business domain.
