#  What This Folder Is For

This folder stores environment documentation. This is a simple folder structure intended to provide you (an AI agent) with basic contextual data about the environment in which you are currently operating. The purpose of this is to avoid confusion.

The folder has two main subfolders: `for-agent` and `for-human.`

Daniel (user) will use `for-agent` to pass context to you about this environment (like hardware specs, system benchmarks, etc). You should populate `for-human` with context for Daniel.

## Markdown Is King

Daniel favors markdown for its easy readability. JSON is great for storing data. You can pass and store context in whatever format you wish. But try to avoid storing lengthy logs. Keep the context pool selective and thin. 

## Example Docs: Human To Agent

Here are some examples of environment docs that Daniel may populate here for your attention:

- Hardware reports 
- System update policies for you to enforce 
- Filesystem structure guidelines

## Example Docs: Agent To Human

Here are some examples of environment docs that YOU (AI agent) may wish to populate here for Daniel:

- Notes about updates you have undertaken to the env 
- Major package installations and their outcome 
- Identified issues in the env for later remediation.
---

# Formatting Process

Please follow these rules when generating documentation about the environment:

## Timestamps

- When creating documentation about this environment, you should always ensure that timestamps are provided. 

Do this in two places:

- 1: Within file names
- 2: Within documents

## Formatting

Use two timestamp formats:

For filenames:

Suffix timestamps by suffixing them to a filename with a hyphen preceding them. E.g.: coderules_080725.md

For documents:

Use a format like this: 08-Aug-2025

The timestamp for documents can be in italics after the title.

----

# Documentation Scope Parameters

The purpose of the environment docs repo is to maintain documentation about the environment (ie, the environment of the host).

This is *NOT* the place to write documentation about specific projects even if they happen to be deployed on the host. For that, use the documentation folders within the project. 