Research Group Wiki - MD Simulation, Machine Learning & AI
===========================================================

A comprehensive, collaborative knowledge base for research groups studying Molecular Dynamics Simulation, Machine Learning, and Artificial Intelligence.

## What is this?

This is a **group wiki** - a centralized resource documentation system for research teams. It contains:

- **Getting Started Guides**: Onboarding and setup instructions
- **Research Fundamentals**: Guides for MD, ML, and AI
- **Tutorials & Workflows**: Step-by-step instructions for common tasks
- **Resources & Tools**: Software installation, datasets, computing infrastructure
- **Research Projects**: Documentation of current group projects
- **Collaboration Practices**: Guidelines, best practices, and tools
- **Troubleshooting**: Solutions to common problems


## Key Sections

- **📚 Getting Started**: New to the group? Start here! [:doc:`docs/source/getting_started`]
- **🧮 Molecular Dynamics**: MD simulation guides, tools, and tutorials
- **🤖 Machine Learning**: ML fundamentals, methods, and frameworks
- **🧠 AI**: Artificial intelligence foundations and applications
- **🔬 Research**: Current projects, publications, and reading lists
- **🛠️ Resources**: Software, datasets, computing infrastructure
- **👥 Collaboration**: Team practices, communication, and guidelines
- **❓ Troubleshooting**: Solutions to common issues


## Getting Started

1. **New member?** Start with :doc:`docs/source/getting_started`
2. **Learning a topic?** Browse MD Simulation, ML, or AI sections
3. **Technical problem?** Check :doc:`docs/source/troubleshooting`
4. **Want to contribute?** See :doc:`docs/source/collaboration/guidelines`


## Structure

This documentation is built with Sphinx and hosted on Read the Docs.

```
docs/
├── source/
│   ├── index.rst              # Main landing page
│   ├── about.rst              # About the group
│   ├── getting_started.rst    # Onboarding guide
│   ├── team.rst               # Team members
│   │
│   ├── md_simulation/         # Molecular Dynamics
│   ├── machine_learning/      # Machine Learning
│   ├── artificial_intelligence/   # AI
│   │
│   ├── research/              # Projects and publications
│   ├── resources/             # Tools, datasets, computing
│   ├── collaboration/         # Team practices
│   │
│   └── troubleshooting.rst    # FAQ & solutions
│
└── requirements.txt           # Sphinx dependencies
```


## Building Locally

Install dependencies:

```bash
pip install -r docs/requirements.txt
```

Build documentation:

```bash
cd docs
make html
```

View in browser:

```bash
open build/html/index.html
```


## Contributing

To improve this wiki:

1. Make changes to `.rst` files in `docs/source/`
2. Follow reStructuredText syntax
3. Test build locally: ``make html``
4. Submit pull request with changes
5. See :doc:`docs/source/collaboration/guidelines` for standards


## Key Features

✨ **Comprehensive**: Covers MD, ML, and AI with depth and breadth

🎓 **Educational**: Tutorials, fundamentals, and learning resources

🤝 **Collaborative**: Best practices for team research and communication

🔧 **Practical**: Real tools, code examples, and troubleshooting

📖 **Accessible**: Easy to search and navigate

🌐 **Open**: Built on open standards (Sphinx, reStructuredText)


## Technologies

- **Sphinx**: Documentation generator
- **Read the Docs Theme**: Professional navigation
- **reStructuredText**: Documentation markup language
- **GitHub**: Version control and collaboration
- **Read the Docs**: Hosted documentation platform


## Support

- **Questions?** Check the :doc:`docs/source/troubleshooting` page
- **Can't find something?** Use the search function
- **Suggestion?** Suggest improvements in group meetings
- **Bug in wiki?** Submit via GitHub issues


## Citation

If you create your own version of this wiki, please cite:

```
Research Group Wiki. Year. Molecular Dynamics, Machine Learning & AI.
Available at: [your hosting url]
```


## License

See LICENSE file for details.


## Acknowledgments

Built as a collaborative resource for the research group.

---

**Last Updated**: 2026

**Maintained By**: TBD

**Questions?** Contact group leads or post in the group communication channel.
