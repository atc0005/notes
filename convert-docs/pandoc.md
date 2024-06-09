# Pandoc

## Generate epub from Markdown

As always the output quality will vary depending on the input formatting, but
this provides a good starting point for offline reading (e.g., phone or
tablet).

```console
cd /path/to/projects/dir
git clone https://github.com/bahamas10/bash-style-guide
cd bash-style-guide
pandoc --metadata author="github.com/bahamas10/bash-style-guide" --metadata title="Bash Style Guide" -s -o bash-style-guide.epub README.md
```

```console
cd /path/to/projects/dir
git clone https://github.com/azet/community_bash_style_guide
cd community_bash_style_guide
pandoc --metadata author="github.com/azet/community_bash_style_guide" --metadata title="Community Bash Style Guide" -s -o community-bash-style-guide.epub README.md
```

## Generate PDF from Markdown

```console
pandoc -s -o output_file.pdf input_file.md
```

## Generate DOCX from Markdown

```console
pandoc -s -o output_file.docx input_file.md
```
