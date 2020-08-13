---
title: JRE
parent: Java
nav_order: 1
---

# Java Runtime Environment
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

If you live in Brazil, you are almost obligated to have a `Java Runtime Environment` (`JRE`) to file your taxes from your desktop computer.

Scroll down to read how I installed it in Portuguese.

## Security

Navigate to `System Settings > Java` and then click to open the `Java Control Panel` in a separate window:

`General`
- Temporary Internet Files: open `Settings...` and uncheck `Keep temporary files on my computer`

`Security`
- Make sure to uncheck `Enable Java content for browser and Web Start applications
- Make sure `Very High` is selected as `Security Level for applications not on the Exception Site list`


## Installation (in Portuguese)

Você, cidadão brasileiro, já deve ter aprendido que a [SERPRO](https://serpro.gov.br) adora Java.

Por isso, infelizmente, precisamos instalar um `Java Runtime Environment` (`JRE`) no macOS se quisermos submeter declarações de impostos à Receita Federal a partir do nosso Mac.

Ao fazer [download do programa da Receita para IRPF](http://www.receita.economia.gov.br/interface/cidadao/irpf), caso você não tenha `JRE` algum instalado, eis a mensagem de erro exibida no macOS Catalina:

![](java-irpf.png)

Para instalar o `JRE` mais recente, navegue a https://www.java.com/en/download/mac_download.jsp e faça download do arquivo `jre-8u251-macosx-x64.dmg`.

> Download Java for Mac OS X
> Recommended Version 8 Update 251 (filesize: 80.65 MB)
> Release date April 14, 2020 

Evite instalar o `JDK` ou coisa parecida. Instale somente o mínimo necessário, isto é, só o tal `JRE`.

Para mais informações sobre Java no macOS, consulte: https://macmagazine.uol.com.br/post/2020/02/26/problemas-ao-rodar-o-irpf-2020-no-mac-confira-as-solucoes/.


## More information about Java updates on the Mac

Bonus read: [Everything you'll wish you didn't know about disabling Java 7 updates
](https://macops.ca/everything-youll-wish-you-didnt-know-about-disabling-java-7-updates/) by Tim Sutton.