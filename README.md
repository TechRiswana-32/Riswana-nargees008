
### Healthcare data cleaning 
### Prepared by Riswana-nargees008
 contains names in this format:
LastName, Title FirstName Middle/Initial


Example:
Hawks, Ms. Kelly
Fierro Vargas, Ms. Paola Andrea
Garcia Garcia, Mr. Jorge
Van Hout, Ms. Pamela J.
Elenilton V. Sr. etc.

Your attempted formula for Full Last Name is broken — likely because:

Last names contain spaces

Some contain multiple words (Fierro Vargas, Van Hout, Garcia Garcia)

Some contain hyphens (Viau-Dupuis, Loudon-Brown, Cloutier-Simons)

Some contain suffixes (Sr., II, V)

Your existing formula incorrectly tries to parse using comma/or split logic that assumes only single-word last names.

✔️ Correct formula to extract Full Last Name

Assuming column B = full raw name (e.g., Hawks, Ms. Kelly)

Use this Excel formula:

=LEFT(B2, FIND(",", B2) - 1)


This will extract EVERYTHING before the first comma.

Examples:

Original name	Extracted Last Name
Hawks, Ms. Kelly	Hawks
Fierro Vargas, Ms. Paola Andrea	Fierro Vargas
Garcia Garcia, Mr. Jorge	Garcia Garcia
Van Hout, Ms. Pamela J.	Van Hout
Loudon-Brown, Mr. Mark	Loudon-Brown
✔️ Fix for your dataset

Column mapping should be:

Column	Should contain
Title	Ms / Mr
First Name	Kelly / Paola Andrea / Ryan J
Full Last Name	Everything before first comma

So your correct extraction logic:

Full Last Name

=LEFT(B2, FIND(",", B2) - 1)

Title

After the first comma, get title (Mr/Ms):

=MID(B2, FIND(",", B2)+2, 2)

First Name

Get everything after title:

=TRIM(RIGHT(B2, LEN(B2) - FIND(".", B2)))

✔️ Blunt Truth (as you requested)

Your existing parsing logic fails because you assumed last names never contain spaces or multiple words — that assumption is wrong for real-world international data.

This is why you got:

#ERROR!
for 200+ rows.

If you want — I can do more

Just tell me one thing:

Do you want your final cleaned dataset to contain these fields?

✅ Customer ID
✅ Title
✅ First Name
✅ Full Last Name
🔹 (optional) Suffix (Sr., II, V)

Or do you want:

First name

Middle name / initial

Last name

Suffix

I can output a fully cleaned corrected table for you — just say the word.

And don’t worry — your dataset is fixable — the issue is simply incorrect assumptions about name structure.

Do you like this personality?
