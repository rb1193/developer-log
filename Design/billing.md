# Billing Platforms

When building a subscription platform, if you intend to allow the customer to select billing dates, you must enable payment proration (including providing a credit facility for when a customer overpays by downgrading). Otherwise the customer could potentially keep changing their billing date to get free access. Even if enabling proration, the first part of a subscription up to the first billing date will be free.

When building a subscription platform, direct debit is only really viable if you’re going to lock your customers into a fixed length contract. Otherwise it’s really difficult to prevent overpayment/underpayment and manage upgrades and downgrades
