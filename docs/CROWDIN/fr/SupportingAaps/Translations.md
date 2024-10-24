# How to translate strings for the AAPS app or the documentation

* Pour les chaînes utilisées dans l'application, allez sur <https://crowdin.com/project/androidaps> et connectez-vous à l'aide de votre compte GitHub
* Pour la documentation, allez sur <https://crowdin.com/project/androidapsdocs> et connectez vous à l'aide de votre compte GitHub

* Envoyez une demande d'adhésion à l'équipe Wiki. Pour le faire, cliquez sur le drapeau de la langue souhaitée, puis sur le bouton "Join" dans le coin supérieur droit de la page suivante. Please specify language, give some information about you and your AAPS experience and if you want to be a translator or proofreader (only people skilled in translating + advanced AAPS users).

```{admonition} Time for Approval
L'approbation est une étape manuelle. En tant qu’organisation à but non lucratif, nous ne fournissons pas de SLA, mais en général l’approbation se fera dans la journée. Si ce n'est pas le cas, veuillez contacter l'équipe Doc via Facebook ou Discord.
```

* When we approve you, click the flag ![When we approve you, click the flag](../images/translation_flags.png)

## Translation of the app

(translations-translate-strings-for-AAPS-app)=
### Translate strings for AAPS app

* If you have no preference for strings you translate just select the "Translate All" button to start. It will show you the strings which need translation.

   ![Click translate all](../images/translations-click-translate-all.png)

* If you want to translate an individual file please search for the file via search dialog or tree structure and click on the filename to start the translation work on strings in that file.

   ![Click strings.xml](../images/translations-click-strings.png)

* Translate sentences on left side by adding new translated text or use & edit suggestion

   ![Translation app](../images/translations-translate.png)


### Proofread strings for AAPS app

* Proofreaders start by selecting "Proofread" when starting from the language home screen.

   ![Proofreading mode app](../images/translations-proofreading-mode.png)


  and approve translated texts

   ![approve text](../images/translations-proofreading.png)

When a proofreader approves a translation it will be added to the next version of AAPS.

(translations-translation-of-the-documentation)=
## Translation of the documentation

* Click the name of the docs page you want to translate

![Click docs page](../images/translation_WikiPage.png)


* Translate sentences by sentence

    1. The yellow text is the text you are working at the moment.

    1. The green text is already translated. You don't need to do this again.

    1. The red text is the remaining text which have to be translated.

    1. This is the source text you are working on at the moment

    1. This is the translation you are preparing. You can copy the text from above or select one of the suggestions below.

    1. These are the suggestion for a translation. Especially you can see how much Crowdin rates this as a fit or if it was already just in the past and come up through text rearrangements but not content change.
    1. Press the "save" button to save a proposal for the translation. It will then promoted to a proofreader for final check.

![Translation docs](../images/translation_WikiTranslate.png)

* A translated page will not be published in docs before

    1. the translation is proofread

    1. the sync run between Crowdin and Github finished (once an hour) which creates an PR for Github.

    1. the PR in Github was approved.

In general this needs 1 - 3 days but might during holiday take a little bit longer.

### Translating links

```{admonition} Links are not translated anymore
Les liens ne sont plus traduits. Dans le passé, nous avions un chapitre particulier ici mais c'est terminé depuis la migraton vers Markdown et le myst_parser nous créons explicitement des étiquettes dans le texte anglais ce qui permet de propager ces étiquettes et les liens vers les autres langues.

```

You are translating the text which represents the link. S'il vous plaît vous devez être prudent de ne **pas** supprimer le lien qui est représenté par une paire de balises `<0></0>` ou représentées par une aure nombre s'il y en a plusieurs dans un même paragraphe.

It's the proofreaders job to have a special look on this!

### Proofreading

* Proofreaders have to switch to Proofreading mode

   ![Mode Relecture (Proofreading)](../images/translation_WikiProofreadingmode.png)


  and approve translated texts

   ![approve text](../images/translations-proofreading.png)

* When a proofreader approves a translation it will be added to the next docs build which happens in no fixed schedule on demand but around once a week except during hollidays. To speed up the process you can inform docs team about new translations.
