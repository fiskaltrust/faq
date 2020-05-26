# FAQ

This repository represents our FAQ collection related to PosCreators, PosOperators, and PosDealers. This means, that the questions and answers here are for public usage.

## Structure

The main directory of this repository contains 3 folders: 

- **qna**: contains markdown files, each representing exactly one question and answer set
- **images**: the answers can embed images that are stored in this folder
- **examples**: contains example markdown files that are linked in the question and answer sets

### Q&A set

Each question and answer set is the single entry stored in one markdown file in the `qna` folder. 

The content of the question and answer set includes:

- **Question**: The main question that a customer may be interested in
- **Alternative questions**: Alternate forms of the main question to be used for better searchability
- **Metadata tags**: Metadata tags used to filter answer choices during a search 
- **Answer**: The answer to the question of this Q&A set

### Metadata tags

This chapter lists all available Metadata tags:

**Language specification**

- lang-en
- lang-at
- lang-fr
- lang-de

**Market specification**

- market-none
- market-all
- market-at
- market-fr
- market-de

**Topic specification**

- middleware
- data-archive
- data-export
- notification
- data-upload
- certification
- offline-SCU
- online-SCU
- webshop
- consulting
- hosting-operations
- bundle-carefree
- bundle-carefree-offline-SCU
- bundle-carefree-online-SCU
- custom-middleware-solution
- portal
- documentation
- website
- security
- performance
- architecture
- tenant management
- cashbox management

**Personas**

- PosCreator
- PosDealer
- PosOperator
- Consultant

Only the above shown tags should be used. If your contribution needs a further tag please let us know by creating an issue with the label "documentation".

## How to contribute

Your contributions to this project will help improve the support of our customers and reduce the work amount for our customer care team. Furthermore, your contribution will help all fiskaltrust colleagues to communicate the same coordinated answers to our customers.

### Getting started

- Make sure you have a [GitHub account](https://github.com/signup/free)
- Ask the the SRE Team to add your GitHub account to the fisklatrust organisation GitHub account (use the "team-sre-inquiry" channel in slack)
- Create a GitHub issue for your contribution, assuming one does not already exist.
- Clearly describe the issue including a link to the referenced file
- Fork the repository on GitHub

### Finding things to work on

The first place to start is always looking over the current GitHub issues you are interested in contributing to. Issues marked with "help wanted" are usually pretty self contained and a good place to get started.

The PM Team also uses these same GitHub issues to keep track of what we are working on. If you see any issues that are assigned to a particular person or have the "in progress" label, that means someone is currently working on that issue. The "next sprint" label means we will likely be working on this issue in the next week or two. The "ready" label means that the issue is one we have prioritized and will be working on in our next sprint or two.

Of course, feel free to make your own issues if you think something needs to added or fixed.

### Making Changes

Create a topic branch from where you want to base your work:
- This is usually the master branch.
- Please avoid working directly on the master branch.

Make sure you have reviewed your changes.

### Submitting Changes

- All content, comments, and pull requests must follow our [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/0/code_of_conduct/).
- Push your changes to a topic branch in your fork of the repository.
- Submit a pull request
- Include a descriptive [commit message](https://github.com/erlang/otp/wiki/Writing-good-commit-messages)
- Changes contributed via pull request should focus on a single issue at a time.
- Rebase your local changes against the master branch. Resolve any conflicts that arise.

### Creating Q&A sets

- Each Q&A set needs its own markdown file in the `qna` directory.
- Filename ([name].md) should at least give some indication of the question. It should start with the country code if market specific ("AT", "FR", "DE") or "General" if not market specific. The single words should be connectd by "-", no blanks. No more than 250 characters are allowed per name. E.g. "General-fiskaltrust-sandbox.md".
- Referenced exaples (e.g. JSON) should be placed in the `examples` folder of the main directory.
- Linked images should be placed in the `images` folder of the main directory.

### Format and content of a Q&A set

- The main question should be placed at the beginning in a chapter called  "## Question". The question itself should be placed below of the chapter name (no markdown, only text, no newlines).
- For each alternative question (Alternate form of the main question to be used for better searchability) add a new chapter called "## Question" and add the question below of the chapter name (no markdown, only text, no newlines).
- Metadata tags: Add a new chapter below the question chapters named "## Metadata tags". List the tags comma separated in one single line below of the chapter name. No newlines and no multiple lines allowed. Use **only the defined tags** (see above). If you need a new tag please add an issue so that we can review and add your tag. Mimimum requirement: add a language specification tag and a market tag.
- Answer: Add a new chapter below the metadata tags chapters named "## Answer". Write the answer in markdown within this chapter.

### Example

[Here](qna/General-fiskaltrust-sandbox.md) you can find an example of how a Q&A set should look like.

## Troubleshooting

Let us know what you're having trouble with! Open an issue or write us in our team-pm-inquiry slack channel.
