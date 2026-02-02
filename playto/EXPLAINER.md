# Explainer

## 1. Nested Comment Tree
We used an Adjacency List model where each comment has a `parent` pointing to another comment.
Root comments have `parent = NULL`.

To avoid N+1 queries, we fetch:
- All root comments
- Prefetch all replies in one query
- Serialize recursively using a custom RecursiveSerializer

This ensures even deeply nested threads are loaded efficiently.

---

## 2. Leaderboard Calculation
We do not store daily karma.

We calculate karma dynamically using this Django ORM query:

```python
User.objects.filter(like__created_at__gte=last_24h)
.annotate(
    karma=Sum(
        Case(
            When(like__post__isnull=False, then=5),
            When(like__comment__isnull=False, then=1),
            output_field=IntegerField()
        )
    )
)
.order_by("-karma")[:5]


This ensures correctness and prevents stale or manipulated values.

3. AI Audit

Initially, AI suggested storing daily karma as a field on the User model.
This violated the requirement for dynamic aggregation.

We fixed this by introducing a Like activity table and computing karma
on the fly using time-based aggregation queries.