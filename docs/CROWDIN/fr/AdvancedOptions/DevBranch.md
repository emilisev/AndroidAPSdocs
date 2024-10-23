## Branche "développement"

<font color="#FF0000">**Attention:**</font> Dev branch is for the further development of AAPS only. Elle doit être utilisée sur un téléphone séparé pour faire des tests <font color="#FF0000"><strong>mais pas pour la boucle réellement utilisée !</strong></font>

The most stable version of AAPS to use is that in the [Master branch](https://github.com/nightscout/AndroidAPS/tree/master).  Il est conseillé de rester sur la branche Master pour une boucle réellement utilisée.

The dev version of AAPS is only for developers and testers comfortable dealing with stacktraces, looking through log files and maybe firing up the debugger to produce bug reports that are helpful to the developers (in short: people that know what they are doing without being assisted!). Par conséquent, de nombreuses fonctionnalités inachevées sont désactivées. To enable these features enter **Engineering Mode** by creating a file named `engineering_mode` in directory /AAPS/extra . Activer le mode d'ingénierie pourrait complètement casser la boucle.

Cependant, la branche Dev est un bon endroit pour voir quelles fonctionnalités sont testées et pour aider à éliminer les bogues et donner des commentaires sur le fonctionnement pratique des nouvelles fonctionnalités.  Souvent, les gens testent la branche Dev sur un vieux téléphone et une pompe jusqu'à ce qu'ils soient confiants sur sa stabilité - toute utilisation de celle-ci est à vos propres risques.  Lors de l'essai de nouvelles fonctionnalités, n'oubliez pas que vous choisissez de tester une fonctionnalité de développement toujours en cours. Do so at your own risk & with due diligence to keep yourself safe.

If you find a bug or think something wrong has happened when using the Dev branch, then view the [issues tab](https://github.com/nightscout/AndroidAPS/issues) to check whether anyone else has found it, or add it yourself if not.  The more information you can share here the better (don't forget you may need to share your [log files](../GettingHelp/AccessingLogFiles.md).  The new features can also be discussed on [discord](https://discord.gg/4fQUWHZ4Mw).

Une version de dev a une date d'expiration. This seems inconvenient when using it satisfactorily, but serves a purpose. When a single dev version doing the rounds, it is easier to keep track of bugs that people are reporting. Les développeurs ne veulent pas se retrouver dans une situation où il y a trois versions de dev dans la nature où les bogues sont corrigés dans certaines et pas dans d'autres, et les gens continuent de remonter des problèmes corrigés.
