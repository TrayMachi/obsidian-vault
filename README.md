# Obsidian Vault

Private Obsidian vault synchronized between devices with Syncthing and backed up with Git.

## Design

- **Obsidian** edits the notes.
- **Syncthing** keeps the live vault files synchronized between devices.
- **Git/GitHub** provides version history and off-device backup.
- Use **one primary computer** as the Git writer (commit/push). Let Syncthing handle the other devices.

## Folder layout

```text
00 Inbox/        Quick capture and unsorted notes
10 University/   University notes and coursework
20 Work/         Work notes and projects
30 Personal/     Personal notes
80 Attachments/  Images, PDFs, and other attachments
90 Templates/    Obsidian templates
Home.md          Vault home page
```

## First computer

Clone this repository into the location where you want the vault:

```bash
git clone git@github.com:TrayMachi/obsidian-vault.git ~/Documents/obsidian-vault
```

Then open Obsidian and choose **Open folder as vault**, selecting `~/Documents/obsidian-vault`.

Use this computer as the primary Git backup writer.

## Syncthing

Share the whole `obsidian-vault` directory through Syncthing. The included `.stignore` prevents Git internals and device-specific workspace state from being synchronized.

Important: Syncthing intentionally does **not** synchronize `.stignore` itself. On devices that receive the vault only through Syncthing (especially Android), create a `.stignore` file in the vault root using the same contents as the one in this repository.

Suggested Android location:

```text
/storage/emulated/0/Documents/Obsidian/obsidian-vault
```

Then open that folder as a vault in Obsidian Android.

## Git backup workflow

On the primary computer:

```bash
cd ~/Documents/obsidian-vault
git status
git add -- <the files you want to back up>
git commit -m "Backup notes"
git push
```

Do not make multiple computers independently commit/push the same live Syncthing vault unless you intentionally want to manage Git conflicts.

## What is intentionally not tracked/synced

Device-specific Obsidian workspace state, Obsidian trash, Syncthing version-history storage, temporary Syncthing files, and common OS metadata are excluded. Plugins, themes, hotkeys, snippets, and other useful `.obsidian` configuration can still be tracked once Obsidian creates them.
