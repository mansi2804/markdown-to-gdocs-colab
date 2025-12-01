Product Meeting Notes → Google Doc
=================================

Brief description
-----------------
Colab-ready workflow that ingests the Product Team Sync meeting notes (Markdown) and converts them into a fully formatted Google Doc via the Google Docs API. The notebook handles authentication, parses headings/bullets/checkboxes, styles `@mentions`, and formats the footer to satisfy the assessment requirements.

Setup instructions
------------------
1. Clone/download this folder so you can push it to your own public GitHub repository (deliverable requirement).
2. Ensure you can sign in to Google Docs with permissions to create/edit docs in the correct Workspace.
3. (Optional) Edit `notes/meeting_notes.md` if you need to tweak the meeting content before running the notebook.
  
Repository contents
-------------------
- `colab/meeting_doc_formatter.ipynb` – Colab notebook that installs dependencies, authenticates, parses Markdown, and generates the Google Doc.
- `notes/meeting_notes.md` – Source Markdown for the Product Team Sync meeting; update this if you need different content.
 
Required dependencies
---------------------
Colab ships with Python 3 and most Google auth packages, but the notebook explicitly installs/upgrades:
- `google-api-python-client`
- `google-auth`
- `google-auth-httplib2`
- `google-auth-oauthlib`

How to run in Colab
-------------------
1. Push this repo to GitHub, then open https://colab.research.google.com/ and choose **File → Open notebook → GitHub** to load `colab/meeting_doc_formatter.ipynb`.
2. Run the dependency installation cell.
3. Execute the authentication cell and allow Colab to access Google Docs with your account.
4. Review or edit the `MEETING_NOTES_MD` constant (or load `notes/meeting_notes.md`) for any meeting updates.
5. Run the final cell to generate the Google Doc; the notebook prints the title, document ID, and shareable link.

Adapting the input
------------------
- To use the bundled Markdown, open `notes/meeting_notes.md` and paste any changes. Then copy/paste the updated text into the `MEETING_NOTES_MD` string in the notebook, or extend the notebook to read directly from the file (see the helper stub inside the notebook).
- Checkboxes written as `- [ ] Task` become true Google Docs checkboxes.
- Mentions written as `@name` are emphasized (bold + blue) to keep assignees visible inside the Doc.

Error handling & logging
------------------------
The helper functions inside the notebook raise descriptive runtime errors if authentication fails, the document cannot be created, or the batch update encounters a Google API issue. Wrap calls in `try/except` (as shown) if you want to handle these errors differently.


Thanks for reviewing!

