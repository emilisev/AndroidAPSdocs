# Objetivos

A AndroidAPS possui uma série de objetivos que precisam ser completados para o encaminhar pelos recursos e configurações de um loop seguro.  Eles garantem que configurou corretamente tudo o que foi detalhado nas seções acima e que entende o que o seu sistema está a fazer e por que assim pode confiar nele.

Se está **a mudar de telemóvel**, então pode [exportar as suas configurações](../Usage/ExportImportSettings.md) para manter o seu progresso através dos objetivos. Não será só o seu progresso através dos objetivos que será salvo, mas também as suas configurações de segurança como o bólus máximo, etc.  Se não exportar e importar as suas configurações então irá precisar de iniciar os objetivos desde o primeiro.  É uma boa ideia fazer o backup das suas configurações \<../Usage/ExportImportSettings.html> \` _ frequentemente precavendo-se.

Se quiser voltar atrás nos objetivos, veja [abaixo como fazê-lo](../Usage/Objectives#go-back-in-objectives).

## Objetivo 1: Configurar a visualização e monitorização, analisando basais e rácios

- Selecione na configuração a fonte de glicose no sangue correta.  Veja [Fonte de GS](../Configuration/BG-Source.md) para mais informações.
- Selecione a bomba correta no Configurador (selecione a bomba virtual se estiver a usar um modelo bomba ainda sem driver da AndroidAPS para loop) para garantir que a bomba pode comunicar com a AndroidAPS.
- Se utilizar a bomba DanaR então certifique-se de ter seguido as instruções para a \` Bomba de insulina DanaR \<../Configuration/DanaR-Insulin-Pump.md> \` _ para garantir o link entre bomba e a AndroidAPS.
- Siga as instruções na página \` Nightscout \<../Installing-AndroidAPS/Nightscout.md> \` _ para garantir que o Nightscout pode receber e exibir esses dados.
- Observe que o URL no NSClient deve ser \*\* SEM /api/v1 /\*\* no final - veja \` NSClient em Preferências \<../Configuration/Preferences#nsclient> \` \_\_.

*Pode ser necessário esperar que a próxima leitura de glicose no sangue chegue antes da AndroidAPS a reconhecer.*

## Objetivo 2: Aprenda a controlar a AndroidAPS

- Execute várias ações na AndroidAPS conforme descrito neste objetivo.

- Clique no texto laranja "Não concluído ainda" para aceder ao que é para fazer.

- Serão fornecidos links para guiá-lo caso não esteja ainda familiarizado com uma ação específica.

  ```{eval-rst}
  .. imagem:: ../images/Objective2_V2_5.png
    :alt: Captura de ecrã do Objetivo 2
  ```

## Objetivo 3: Prove o seu conhecimento

- Passe um teste de escolha múltipla testando o seu conhecimento da AndroidAPS.

- Clique no texto laranja "Não concluído ainda" para aceder à página com a pergunta e as opções de resposta.

  ```{eval-rst}
  .. imagem:: ../images/Objective2_V2_5.png
    :alt: Captura de ecrã do Objetivo 3
  ```

- Serão fornecidos links para guiá-lo caso ainda não tenha a certeza sobre as respostas corretas.

- As perguntas para o objetivo 3 foram completamente reescritas por falantes nativos a partir da AAPS 2.8. Os novos cobrem os mesmos tópicos básicos e mais alguns novos.

- Estas novas perguntas levarão a algumas perguntas não respondidas mesmo tendo concluído com sucesso o objetivo 3 em versões anteriores.

- perguntas não respondidas só o afetarão se iniciar um novo objetivo. Por outras palavras: Se já completou todos os objetivos, pode esperar e responder às novas perguntas mais tarde, sem perder as funções da AAPS.

## Objetivo 4: Iniciar um loop aberto

- Selecione Loop Aberto a partir de Preferências, ou pressionando e segurando o botão Loop em cima esquerda da tela inicial.
- "Navegue" pelas [Preferências](../Configuration/Preferences.md) para configurar a APS para si.
- Manualmente defina pelo menos 20 das basais temporárias sugeridas ao longo de um período de 7 dias; insira-os na sua bomba e confirme na AndroidAPS que as aceitou.  Garanta que esses dados estão registados na AndroidAPS e no Nightscout.
- Enable [temp targets](../Usage/temptarget.md) if necessary. Use hypo temp targets to prevent that the system will correct too strong because of a raising blood glucose after a hypo.

### Reduce number of notifications

- To reduce the Number of decisions to be made while in Open Loop set wide target range like 90 - 150 mg/dl or 5,0 - 8,5 mmol/l.

- You might even want to wider upper limit (or disable Open Loop) at night.

- In Preferences you can set a minimum percentage for suggestion of basal rate change.

  ```{image} ../images/OpenLoop_MinimalRequestChange2.png
  :alt: Open Loop minimal request change
  ```

- Also, you do not need to act every 5 minutes on all suggestions...

## Objective 5: Understanding your open loop, including its temp basal recommendations

- Start to understand the thinking behind the temp basal recommendations by looking at the [determine basal logic](https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/Understand-determine-basal.html) and both the [forecast line in AndroidAPS homescreen](../Getting-Started/Screenshots#prediction-lines)/Nightscout and the summary of outputs from the calculations in your OpenAPS tab.

You will want to set your target higher than usual until you are confident in the calculations and settings.  System allows

- a low target to be a minimum of 4 mmol (72 mg/dl) or maximum of 10 mmol (180 mg/dl)
- a high target to be a minimum of 5 mmol (90 mg/dl) and maximum of 15 mmol (225 mg/dl)
- a temporary target as a single value can be anywhere in the range of 4 mmol to 15 mmol (72 mg/dl to 225 mg/dl)

The target is the value that calculations are based on, and not the same as where you aim to keep your blood glucose values within.  If your target is very wide (say, 3 or more mmol \[50 mg/dl or more\] wide), you will often find little AAPS action. This is because blood glucose is eventually predicted to be somewhere in that wide range and therefore not many fluctuating temporary basal rates are suggested.

You may want to experiment with adjusting your targets to be a closer together range (say, 1 or less mmol \[20 mg/dl or less\] wide) and observe how the behavior of your system changes as a result.

You can view a wider range (green lines) on the graph for the values you aim to keep your blood glucose within by entering different values in [Preferences](../Configuration/Preferences.md) > Range for Visualisation.

```{image} ../images/sign_stop.png
:alt: Stop sign
```

### Stop here if you are open looping with a virtual pump - do not click Verify at the end of this objective.

```{image} ../images/blank.png
:alt: blank
```

## Objective 6: Starting to close the loop with Low Glucose Suspend

```{image} ../images/sign_warning.png
:alt: Warning sign
```

### Closed loop will not correct high BG values in objective 6 as it is limited to low glucose suspend. High BG values have to be corrected manually by you!

- Prerequisite: You need a good profile (basal, ISF, IC) already working in AndroidAPS to start with Loop in Low Glucose Suspend mode. Otherwise you can run in a hypo which you have to manually correct. This will help you a lot to avoid having to treat a low glucose over a period of 5 days. **If you are still having frequent or severe low glucose episodes then consider refining your DIA, basal, ISF and carb ratios and do NOT start objective 6 at this time.**
- You don't have to change your settings now. During objective 6, the maxIOB setting is internally set to zero automatically. **This override will be reversed when moving to objective 7.**
- The system will override your maxIOB settings to zero, which means if blood glucose is dropping it can reduce basal for you. If blood glucose is rising then it will only increase basal if the basal IOB is negative from a previous Low Glucose Suspend. Otherwise basal rates will remain the same as your selected profile. **That means that you have to manually handle high values with insulin corrections.**
- If your basal IOB is negative (see screenshot below) a TBR > 100% can be issued also in objective 6.

```{image} ../images/Objective6_negIOB.png
:alt: Example negative IOB
```

- Set your target range slightly higher than you usually aim for, just to be safe and have a bit more scurity buffer.
- Enable 'Low Glucose Suspend' mode either by by pressing and holding the Loop icon at the top right corner of the home screen and selecting the Loop - LGS mode icon.
- Watch how temporary basals are active by viewing the blue basal text on the homescreen or the blue basal render on the homescreen graph.
- You may temporarily experience spikes following treated hypos without the ability to increase basal on the rebound.

## Objective 7: Tuning the closed loop, raising maxIOB above 0 and gradually lowering BG targets

- Select 'Closed Loop' either from [Preferences](../Configuration/Preferences.md) or by pressing and holding the Loop icon at the top right corner of the home screen, over a period of 1 day.

- Raise your 'Maximum total IOB OpenAPS can’t go over' (in OpenAPS called 'max-iob') above 0. The default recommendation is "average mealbolus + 3x max daily basal" (for the SMB algorithm) or "3x max daily basal" (for the older AMA algorithm) but you should slowly work up to this until you know your settings work for you (max daily basal = the maximum hourly value in any time segment of the day).

  This recommendation should be seen as a starting point. If you set to the 3x and you are seeing moves that push you too hard and fast then lower that number. If you are very resistant, raise it very little at a time.

  ```{image} ../images/MaxDailyBasal2.png
  :alt: max daily basal
  ```

- Once confident on how much IOB suits your looping patterns, then reduce your targets to your desired level.

## Objective 8: Adjust basals and ratios if needed, and then enable autosens

- You can use [autotune](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html) as a one off to check your basals remain accurate or do a traditional basal test.
- Enable [autosens](../Usage/Open-APS-features.md) over a period of 7 days and watch the white line on the homescreen graph show how your sensitivity to insulin may be rising or falling as a result of exercise or hormones etc. and keep an eye in the OpenAPS report tab how AndroidAPS is adjusting the basals and/or targets accordingly.

*Don’t forget to record your looping in* [this form](https://bit.ly/nowlooping) *logging AndroidAPS as your type of DIY loop software, if you have not already done so.*

## Objective 9: Enabling additional oref1 features for daytime use, such as super micro bolus (SMB)

- You must read the [SMB chapter in this wiki](../Usage/Open-APS-features#super-micro-bolus-smb) and [chapter oref1 in openAPSdocs](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html) to understand how SMB works, especially what's the idea behind zero-temping.
- Then you ought to [rise maxIOB](../Usage/Open-APS-features#maximum-total-iob-openaps-cant-go-over-openaps-max-iob) to get SMBs working fine. maxIOB now includes all IOB, not just added basal. That is, if given a bolus of 8 U for a meal and maxIOB is 7 U, no SMBs will be delivered until IOB drops below 7 U. A good start is maxIOB = average mealbolus + 3x max daily basal (max daily basal = the maximum hourly value in any time segment of the day - see [objective 7](../Usage/Objectives.md#objective-7-tuning-the-closed-loop-raising-max-iob-above-0-and-gradually-lowering-bg-targets) for an illustration)
- min_5m_carbimpact default in absorption settings has changed from 3 to 8 going from AMA to SMB. If you are upgrading from AMA to SMB, you have to change it manually.

## Objective 10: Automation

- You have to start objective 10 to be able to use [Automation](../Usage/Automation.md).
- Make sure you have completed all objectives including exam [../Usage/Objectives#objective-3-prove-your-knowledge](../Usage/Objectives.md#objective-3-prove-your-knowledge).
- Completing previous objectives will not effect other objectives you have already finished. Vai manter todos os objetivos acabados!

## Go back in objectives

If you want to go back in objectives for whatever reason you can do so by clicking at "clear finished".

```{image} ../images/Objective_ClearFinished.png
:alt: Go back in objectives
```

## Objectives in Android APS before version 3.0

One objective was removed when Android APS 3.0 was released.  Users of Android APS version 2.8.2.1 who are on older Android software (i.e. earlier than version 9) will be using an older set of objectives which can be found [here](../Usage/Objectives_old.md).