# Instructions for using Template

## Manual Tasks After Using Template

Manual changes to be made to the new repository.

### 1. Create branch on GitHub

![image](https://github.com/user-attachments/assets/0d436459-20c8-4057-8bdb-9e8b5a28fc35)

### 2. Create Initial Tag

Revision structure is based on the related software major revision number.

e.g . If the document relates to Tercen and Tercen is at revision 0.15.5 then the document is 0.15.x 

The Minor revision is the document revision.

### 3. Changes to mkdocs.yaml

Change the following to what is relevant to the new repository. Replace the "administrators_guide" below references.

site_name: Tercen Administrators Guide  
repo_url: https://github.com/tercen/administrators_guide  
repo_name: tercen/administrators_guide  
repository: tercen/administrators_guide  

## Markdown Examples

Bolded List

- **Yellow:** Factor names for id codes and experimental data.
- **Green:** Factor names for measurements.
- **Blue, Beige, Orange:** Individual records with data.

Quote feature for drag and drop function

_**From Gather**_
> Value to Y-Axis.  
> Variable to Row.

Table

| Name                  | Good looking score | Text    |
| --------------------- | ------------------ | ------- |
| Tommy                 | 7                  |         |
| Hansel from Zoolander | 933                |         |
| You                   | 10                 | ASFSADF |

## Navigation Table in mkdocs.yaml

When finished creating the individual Markdown pages to a tutorial they have to me referenced in the mkdocs.yaml file.

The top level of the hierarchy (Introduction & Tutorial) is displayed in tabs in the MKDocs deployment.
Subsequent indents become the right sidebar navigation of a Tab.
An In-page navigation is generated in the left sidebar from the markdown headings in the document.

```nav:
  - Introduction: index.md
  - Tutorial:
      - Create a Project: create_a_project.md
      - Upload Data: upload_data.md
      - Basic Analysis - Workflow: workflow.md
      - Using Operators: operators.md
      - Join Data files: join.md
      - Export a Data Table: export_data.md
      - Perform a Gather: gather.md
      - Apply a Filter: filter.md
      - Collaboration Tips: collaborate.md
```

> [!WARNING]
> DON'T DELETE THE `package.json` file!


## Local Build Instructions (Linux)

```shell
docker run --rm -it \
   -p 8000:8000 \
   -v ${PWD}:/docs \
   -e MKDOCS_GIT_COMMITTERS_APIKEY=$GITHUB_TOKEN \
   --entrypoint sh \
   squidfunk/mkdocs-material

pip install mike
pip install mkdocs-git-committers-plugin-2
pip install mkdocs-git-revision-date-localized-plugin
 
mkdocs serve --dev-addr=0.0.0.0:8000
```
