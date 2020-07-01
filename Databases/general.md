# General Database Usage Information

It is only valuable to index foreign key columns when one of the following statements is true:

1. You need to join on the foreign key field (e.g. when looking up children from a column on the parent other than the primary key)
2. You are likely to delete a row in the target table (e.g. any time you set the onDelete option to anything other than RESTRICT)
