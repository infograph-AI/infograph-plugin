---
name: infograph
description: Use this skill when the user asks about their own business numbers or data, such as sales, revenue, orders, customers, marketing spend, finance or product usage, held in their Infograph account (uploaded spreadsheets and files, and data synced from their apps and databases), or asks for a dashboard, report, chart or analysis of that data. Do not use it for general knowledge, or to change anything in the apps the data came from.
---

# Working with Infograph

Infograph holds the user's files and the data from their connected apps and databases as tables in
one private data lake. You work in the one account the user chose when they signed in.

1. Call `listFiles` to see the data items. Each has an 8 character ref: copy it exactly.
2. Call `previewFile` on the items you will use, to see their real columns and sample rows.
3. Call `sqlQuery` with DuckDB SQL, naming each table as `{{ref}}`. Aggregate in SQL: the query
   runs over every row, and you see at most 250 rows of the result.
4. To build something the user can keep, call `createArtifact`, read the brief it returns, then
   write the files with `updateCode`. Give the user the link from the answer.
5. To add a file from this machine as data, call `createUploadUrl`, PUT the file to the address it
   gives, then call `confirmUpload`.
6. Share with anyone with the link, or delete anything, only when the user asked for it.

Infograph cannot change anything in the apps the data came from. If the user asks for that, say so.
