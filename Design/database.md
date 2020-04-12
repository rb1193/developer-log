# Database Design

Eloquent and Spot don’t do much of their work via SQL when it comes to eager loading relations. Eloquent does seem to do a join but then has to match the related entities up to the base entities anyway. Spot runs a separate query to load the relations.

Good article on [the Active Repository anti-pattern](https://adamwathan.me/2015/02/14/active-repository-is-an-anti-pattern/), though it doesn’t offer any solution to the issue of calling $model->save() in the controller for a simple insert or update

When you want to avoid adding a soft delete or status column to a database table because it’s going to make constraints inelegant and/or fragile to enforce, consider separating the table into a table for each state, e.g. active_subscriptions, cancelled_subscriptions. [Source](https://richarddingwall.name/2009/11/20/the-trouble-with-soft-delete/)
