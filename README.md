# Creating Profiles for mdEditor
Profiles in mdEditor are settings you can use during the metadata editing process in mdEditor to simplify data entry. They are composed of two parts: a profile definition, which determines which fields are displayed during an edit session, and a schema, which determines which fields are required. mdEditor has four built-in profiles that can be used when editing metadata: Basic, Full, Project, and Product. In addition to these built-in profiles, custom profiles can be developed and loaded into mdEditor.

Profiles can be developed for metadata records and data dictionaries. It is currently not possible to develop profiles for use during contact creation.

Profile definitions and schema should be hosted online (i.e. on GitHub) to be used in mdEditor. Keep in mind that it may take up to 5 minutes for changes to profile definitions and schema to be reflected on mdEditor. I recommend using the profile definition or schema's version to keep track of updates.

## Contents
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->
- [Creating Profiles for mdEditor](#creating-profiles-for-mdeditor)
- [Contents](#contents)
- [Known Issues](#known-issues)
- [Profile Definitions](#profile-definitions)
	- [Profile Definition Components](#profile-definition-components)
	- [Identifiers](#identifiers)
- [Adding Profiles to mdEditor](#adding-profiles-to-mdeditor)
	- [Add a profile definition to mdEditor](#add-a-profile-definition-to-mdeditor)
	- [Add a profile to mdEditor](#add-a-profile-to-mdeditor)

<!-- /TOC -->
## Known Issues
See [Issues](https://github.com/twisneskie/mdEditor-profile-creation/issues) for the known list of fields and sections that don't function as expected. If you encounter any errors when using the full profile, please submit an Issue.

## Profile Definitions
The full profile outline (full-profile-outline.json) provides the full set of fields and sections used in creating profile definitions for the metadata creation program, mdEditor.

The full profile outline can be found [here](https://raw.githubusercontent.com/twisneskie/mdEditor-profile-creation/main/full-profile-outline.json). Copy the contents of the profile definition to your preferred code editor to modify it.

Changing the file so that a field is set to "false" will hide that field. Fields that are set to "true" will be displayed. All fields are set to "true" by default, so omitting them from the file will result in the omitted field being displayed. You can set a section to "false" rather than turning off every field individually to remove entire sections. See the [USFWS Alaska Region Project Profile Definition](https://raw.githubusercontent.com/twisneskie/ak-md-profiles/dev/ak-proj-profile.json) for an example of a complete profile definition.

### Profile Definition Components
There are a number of key components found within the profile definition.
- **identifier**: a unique identifier/name for the profile definition
- **namespace**: the scope for the identifier
- **title**: a title for the profile definition
- **description**: a description of what the profile definition should be used for
- **version**: the version number of the profile definition.
- **components**: the section of the profile definition that states which fields and sections should be hidden. This is subdivided into record (holds fields for metadata records) and dictionary (holds fields for data dictionary records).
- **nav**: this section can be used to hide or change the tool tips for sections within an edit session (e.g. Main, Metadata, Keywords). Removing a section will hide the whole tab. Changing the title or tip will change how the section is named or what the tooltip displays, respectively. This is also subdivided into record and dictionary sections.

### Identifiers
mdEditor uses three separate field names to represent identifier sections: "identifier", "identifierSimple", and "identifierShort".

identifierShort is the most obvious difference. It displays fewer fields than identifier or identifierSimple: just Identifier, Namespace, Version, and Description.

![identifierShort](pictures/identifierShort.png)


Identifier and identifierSimple both show all of the identifier fields (all listed above + authority), but change how mdEditor actually displays them. identifierSimple shows the identifier subsection as a pop-up window.

![identifierSimple](pictures/identifierSimple.png)

identifier brings you to a separate page to fill out the subsection.

![identifier](pictures/identifier.png)

This full profile outline sets all three types of identifier sections to "true", resulting in three identifier sections when using this profile definition.

In nearly every instance where there is a choice between the three options, identifier will be the default (exceptions include: Taxonomy/Taxonomic System/Citation/Identifier and Documents/Identifier which both have identifierSimple as the default). The default identifier option must be set to "false" when using another identifier style, or both types of identifier options will be shown.

## Adding Profiles to mdEditor
To use a profile during metadata editing, you will need to add at least a profile definition to a profile. A profile can be used without a schema, or one or one or more schema can be attached.

### Add a profile definition to mdEditor
1. Go to Settings/Profiles/Manage Definitions.
2. Select "Add Definition".
3. Select "Imported" tab.
3. Enter URL to profile definition.
4. Enter an optional alias (the alias replaces the definition title).
5. Select "Save definition". You should receive a notification that the profile has been downloaded and profile information will be displayed on the tab.

### Add a profile to mdEditor
1. Go to Settings/Profiles.
2. Select "Add Profile".
3. Enter a "Title" (displayed in profile selection field).
4. Select a "Profile Definition" from dropdown list (either the definition title or the alias entered in the previous step will be displayed).
5. Optional: Add a description (displayed when cursor hovers over "?" in the profile selection field).
4. Optional: Identify a schema from the "Selected Schema" list and select "Add" (NOTE: If you skip this step you will see a "No schemas have been assigned" warning. It is ok to ignore this warning if you do not want to assign a schema to the profile).
5. Select "Save Profile".

**Changes made to a existing profile may not be reflected until the editor is reloaded.**
