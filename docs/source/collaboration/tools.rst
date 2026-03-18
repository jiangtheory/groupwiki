Collaboration Tools
===================

Communication Platforms
-----------------------

**Slack**

Primary communication channel for group.

- **Workspace**: TBD
- **Sign up**: Invitation from group leads
- **Channels**: Organized by topic

**Main Channels**

- `#general`: Announcements and general discussion
- `#research`: Research discussion and updates
- `#random`: Off-topic chat
- `#help`: Technical questions
- `#papers`: Paper discussions
- `#jobs`: Job opportunities
- `#events`: Group events and conferences

**Slack Etiquette**

- Use threads for conversations
- Search before asking duplicates
- Use appropriate channels
- Keep conversations professional
- Pin important information


**Email**

For formal communication:

- Group email lists: TBD
- Reply-all: Use carefully
- Subject lines: Clear and descriptive
- Keep it concise


Version Control & Code Sharing
------------------------------

**GitHub**

Our primary code repository platform.

- **Organization**: TBD
- **Repositories**: See wiki home page
- **Access**: Ask group leads


**Repository Structure**

Each project should have:

- `README.md`: Project description
- `requirements.txt`: Dependencies
- `LICENSE`: Open source license
- `docs/`: Documentation
- `src/` or `code/`: Source code
- `tests/`: Test files
- `.gitignore`: Don't commit sensitive files


**GitHub Workflow**

1. Clone repository
2. Create feature branch: `git checkout -b feature/name`
3. Make commits with clear messages
4. Push to GitHub
5. Create pull request
6. Request review
7. Address feedback
8. Merge when approved

For detailed guidelines, see :doc:`guidelines`


**Access & Permissions**

- Request access from repository owner
- Use SSH keys for authentication
- Follow branch protection rules
- Don't push directly to main


Data Sharing & Storage
----------------------

**Shared Storage**

TBD - Add storage information:

- **Location**: TBD
- **Size limit**: TBD
- **Backup**: TBD
- **Access**: TBD


**File Organization**

Keep shared data organized:

.. code-block:: text

   shared_storage/
   ├── simulations/
   ├── data/
   ├── analysis/
   └── papers/


**Data Protocols**

- Use clear naming: `project_date_description.ext`
- Document data in README
- Don't duplicate large files
- Archive completed projects
- Use version numbers when needed


Document Collaboration
----------------------

**Google Drive**

For collaborative document writing:

- **Workspace**: TBD
- **Access**: Ask group leads
- Real-time editing
- Comments and suggestions


**OneDrive/SharePoint**

TBD - If used by institution


**Overleaf**

For collaborative LaTeX manuscripts:

- Free accounts available
- Real-time editing
- Git integration
- Version history


**Google Docs Best Practices**

- Use consistent formatting
- Comment instead of editing others' work
- Track changes
- Share with appropriate permissions
- Archive completed documents


Project Management
------------------

**GitHub Issues**

For task tracking within repos:

- Create issue for each task
- Use labels and milestones
- Assign to responsible person
- Close when complete


**GitHub Projects**

Kanban-style boards for workflow:

- Create for projects
- Move issues through columns
- Track progress
- See big picture


**Trello** (if used)

TBD - For overall lab management


Video & Meetings
----------------

**Zoom**

For remote meetings:

- Meeting links: TBD
- Calendar invites include Zoom link
- Join 5 min early
- Use video and clear audio
- See virtual meeting tips: :doc:`meetings`


**Google Meet**

Alternative video platform:

- Access via Google account
- No download required
- Good for smaller meetings


**Scheduling**

Use shared calendar:

- Check availability
- Propose times on Doodle
- Send calendar invites
- Include agenda


Lab Notebook & Experiment Tracking
-----------------------------------

**Electronic Lab Notebook (ELN)**

TBD - If group uses ELN:

- Platform: TBD
- Setup instructions: TBD
- Best practices: TBD


**Jupyter Notebooks**

For computational work:

- Good for exploratory analysis
- Share with collaborators easily
- Version control with Git
- Export as HTML/PDF


**Note-Taking Tools**

**Obsidian**: Personal knowledge management

- Local storage
- Markdown format
- Linking between notes
- Sync across devices (with paid plan)

**Notion**: Team workspace

- Shared databases
- Templates
- Good for team wiki
- Free for students


External Services
-----------------

**Preprint Servers**

Share work before publication:

- **arXiv**: https://arxiv.org/ (multidisciplinary)
- **bioRxiv**: https://www.biorxiv.org/ (biology)
- **chemRxiv**: https://chemrxiv.org/ (chemistry)


**Figshare**

Share data, figures, and papers:

- Get DOI for citations
- Easy data archiving
- Public or restricted


**Zenodo**

Research data repository:

- Government-supported
- Long-term preservation
- DOI and citation tracking


**PubPeer**

Post-publication peer review:

- Comment on published papers
- Community discussion
- Anonymous option available


Institutional Tools
-------------------

TBD - Add institution-specific tools:

- Library access: TBD
- Computing portal: TBD
- HR systems: TBD


Passwords & Security
---------------------

**Password Management**

- Use password manager (LastPass, 1Password, Bitwarden)
- Strong passwords (16+ characters)
- Don't share passwords
- Enable 2FA when available


**SSH Keys**

For secure GitHub access:

1. Generate key: ``ssh-keygen -t rsa -b 4096``
2. Add to GitHub: Settings → SSH keys
3. Use for cloning: ``git clone git@github.com:...``


Security Best Practices
-----------------------

- Don't commit secrets/passwords to Git
- Use `.gitignore` for sensitive files
- Consider using `.env` files (not committed)
- Check for credential leaks before committing
- Use GitHub secrets for CI/CD


Getting Help
-----------

**Technical Issues**

1. Search existing issues
2. Ask in #help channel
3. Email leads if critical
4. Document and share solution


**Collaboration Issues**

- Talk to involved parties directly
- Bring to group leads if needed
- See :doc:`guidelines` for conflicts


Recommended Tools Checklist
---------------------------

□ Slack installed and joined
□ GitHub account created and SSH setup
□ Email working
□ Zoom link saved
□ Access to shared storage
□ Git installed locally
□ IDE or editor installed
□ Jupyter working


Questions?
----------

- Ask in #help channel
- Email group leads
- See other collaboration pages: :doc:`index`
