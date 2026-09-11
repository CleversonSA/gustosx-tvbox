# GUSTOSX para TV Box

## Introdução

O **GustoSX para TVBox ** é uma distribuição Linux baseada no Armbian com um único objetivo: dar uma antiga e defasada TV Box um "sabor" MSX dedicado.

O projeto é baseado em outro que criei para processadores x86 32bits [que pode ser conferido aqui](https://github.com/CleversonSA/gustosx)

> **Importante:** este é um projeto experimental e comunitário. Não utilize a distribuição para armazenar dados sensíveis ou críticos. Faça sempre backup dos seus arquivos e do firmware original antes de modificar o equipamento.

---

# Instalação

## Leia antes de começar

**ATENÇÃO: A INSTALAÇÃO DA IMAGEM NA MEMÓRIA INTERNA DA TV BOX PODE APAGAR O SISTEMA ORIGINAL, INCLUINDO O ANDROID, SEUS APLICATIVOS, CONFIGURAÇÕES E DADOS.**

A instalação é de responsabilidade do usuário. Uma imagem incompatível, uma escolha incorreta do dispositivo de destino ou uma interrupção durante a gravação podem fazer com que a TV Box deixe de iniciar. Por sua conta em risco!

## Compatibilidade

**Este projeto foi testado somente em TV Boxes da série Rockchip RK322x.**

O desenvolvimento e os testes iniciais foram realizados em uma TV Box MXQ Pro 5G 4K equipada com processador RK3228A, que é a única que tinha em mãos no momento (sério não to afim de gastar muito com isso :) )

Por esse motivo, o fato de uma TV Box possuir o processador RK3228A, RK3228B ou RK3229 não garante que a imagem funcionará corretamente. Também não há garantia de compatibilidade com outros processadores Rockchip, Amlogic, Allwinner ou qualquer outra família.

**Não instale esta imagem em uma TV Box que não pertença à série RK322x.**

## Hardware necessário

- TV Box equipada com processador da família Rockchip RK322x.
- 2 cartões SD ou 2 pendrives, ou 1 pendrive e 1 SD, enfim, 1 para o multitool e imagem e outro, opcional, para instalar as ROMs das máquinas e jogos. Garanta que pelo menos tenham entre 4GB a 8GB de armazenamento.
- Monitor ou TV com entrada HDMI.
- Teclado USB para a instalação e utilização inicial (Obs: dependendo da caixinha utilizada, nem todo teclado mecânico funcionará, somente testando mesmo).
- Fonte de alimentação adequada para a TV Box (a minha foi 5V 2A)

## Software necessário

- Programa para gravar imagens em cartões microSD, como Etcher, Raspberry Pi Imager ou ferramenta equivalente.
- Imagem do Multitool para RK322x.
- Imagem do GustoSX para RK322x.

### Downloads

**Multitool** 
Família de processador|link|
----------------------|----|
rk322x|[Baixar Multitool](LINK_DO_MULTITOOL)|

**Imagem GustoSX** 
Família de processador|Versão|Link|
----------------------|------|----|
rk322x|0.10.4|[gustosx-tvbox-rk322x-0.10.4.gz](LINK_DA_IMAGEM_GUSTOSX)|


---

## 1. Preparando o cartão microSD

Baixe a imagem do Multitool e grave-a no cartão microSD utilizando o programa de sua preferência.

Certifique-se de selecionar o cartão correto. A gravação apagará os dados existentes nele.

Após a gravação, remova o cartão com segurança e insira-o na TV Box desligada. Conecte o teclado e a saída HDMI e, em seguida, ligue a alimentação.

Se o hardware for compatível e o processo de boot ocorrer corretamente, o ambiente do Multitool será iniciado.


---

## 2. Fazendo o backup do firmware original

**Este procedimento deve ser realizado antes de qualquer gravação ou apagamento da memória interna.**

No menu do Multitool, selecione a opção de backup da memória flash, normalmente identificada como **Backup flash**.

Dê um nome para o backup (ex: tvbox-ddmmaa-backup) e pressione ENTER

Aguarde a conclusão do processo, deve demorar em torno de 20min a 30min pelos testes que fiz.

Os backups ficam dentro da pasta BACKUP do volume MULTITOOL, ao ler o cartão no computador.

**Não prossiga com a instalação se o backup falhar ou se você não tiver certeza de que ele foi salvo corretamente. Sério :)**

---

## 3. Preparando a imagem do GustoSX

Baixe a imagem do GustoSX pelo link disponibilizado acima.

Coloque o arquivo na pasta `images` da partição de dados do cartão do Multitool, conforme as instruções da versão utilizada. Se necessário, descompacte o arquivo antes de copiá-lo.

A estrutura esperada será semelhante a:

```text
Cartão Multitool
└── images/
    └── gustosx-tvbox-rk322x-x.xx.x.gz
```


---

## 4. Gravando o GustoSX na TV Box

Com o cartão preparado e o backup já realizado, inicie novamente o Multitool.

Selecione a opção de gravação de imagem na memória interna, normalmente identificada como **Burn image to flash**, e escolha a imagem do GustoSX.

Confirme cuidadosamente o dispositivo de destino apresentado pelo Multitool. Dependendo da TV Box, a memória interna pode ser eMMC ou NAND, e os nomes dos dispositivos podem variar.

Após confirmar a gravação, aguarde até que o processo seja concluído. Não desligue a TV Box nem remova o cartão durante a operação.

Ao finalizar, utilize a opção de desligamento do Multitool, remova o cartão microSD e ligue novamente a TV Box.

---

## 5. Primeiro boot

Na primeira inicialização, o GustoSX poderá levar mais tempo para iniciar, pois o sistema poderá realizar ajustes e redimensionamento do sistema de arquivos.

Aguarde a conclusão do boot (+- 2min). Se tudo estiver correto, o OpenMSX será inicializado automaticamente com a imagem do C-BIOS e pronto para uso.

---

# Utilizando o emulador OpenMSX puro somente com C-BIOS

É possível utilizar o OpenMSX puro, sem  máquinas proprietárias, você precisará de um mouse e um pouco de prática para o uso dos menus do emulador.

## 1. Preparando um pendrive/SD card

Certifique-se que o pendrive ou cartão SD esteja formatado com FAT32, exFAT costuma a dar problemas na montagem automática nessa disto.

Coloque as ROMs dos jogos que deseja na pasta raiz do pendrive.

Com o emulador iniciado, coloque o pendrive na TVBox e aguarde alguns segundos. Não será emitido nenhum aviso na tela.

O pendrive é automaticamente montado na pasta  ```/mnt/storage2```

Basta selecionar as ROMS e jogar. Segue uma boa referência para jogos do MSX:

- [Jogos MSX](https://www.file-hunter.com)

---

# Experimentando o sabor MSX completo

O projeto não tem como objetivo distribuir ROMs proprietárias de máquinas ou jogos. O usuário deverá fornecer os arquivos necessários para utilizar os perfis de máquinas desejados, respeitando os direitos autorais e a legislação aplicável.

### 1. O projeto não tem nenhuma ROM de máquina, então você precisará localizar e baixar as seguintes ROMS de máquina para ativar os recursos principais da distro:

- Expert Gradiente XP800 (obrigatório no primeiro uso)
- Hotbit Sharp HB-8000 (opcional)
- DDX 3.0 (obrigatório no primeiro uso)
- Nextor (obrigatório para o suporte a HD e no primeiro uso)

### 2. Você pode encontrar referências nesses sites indicados:

- [Nextor](https://github.com/Konamiman/Nextor/releases)
- [Hardware e software relacionado a MSX](https://www.msxpro.com)
- [Jogos MSX](https://www.file-hunter.com)

### 3. Instalando ROMs de jogos e máquinas

- 1. Certifique-se que o pendrive ou cartão SD esteja formatado com FAT32, exFAT costuma a dar problemas na montagem automática nessa disto.

- 2. Na pasta raiz do pendrive crie a pasta **systemroms** 

- 3. Baixe as ROMs das máquinas e NEXTOR necessárias e coloque elas dentro da pasta **systemroms**. NÃO COLOQUE AS ROMS DE JOGOS NESTA PASTA!

- 4. Na pasta raiz do pendrive, crie uma pasta chamada GAMES dentro pasta **msxhd** e nesta pasta coloque as ROMs que baixar. É essa pasta que o SofaRun irá procurar no início da distro.

- 5. Desligue a TVBox, aguarde alguns segundos, coloque o pendrive e a ligue novamente. Depois de alguns segundos, se estiver com as ROMs corretas, será iniciado o emulador com um programa em basic chamado **AVISO DE SISTEMA**, que copiará TODOS os arquivos que estiverem na pasta **msxhd** para o hd virtual **hd.dsk** deixando permanente na TVBox.

- 6. Se tudo der certo, depois de algum tempo, o SofaRun será inicializado automaticamente. Nesse momento você pode desconectar o pendrive. 


Lembre-se, sempre que precisar do pendrive, ele é automaticamente montado na pasta ```/mnt/storage2```, sendo acessível a qualquer momento.


---

# Arquitetura e desenvolvimento

## Estrutura base

A versão para TV Box utiliza os seguintes componentes:

- Armbian para placas RK322x.
- Debian 13 Trixie.
- Kernel Linux da linha 6.x.
- Arquitetura ARM.
- Xfce personalizado.
- OpenMSX compilado para a plataforma.
- Scripts Shell para automação e integração do ambiente.
- Personalizações de boot e identidade visual do GustoSX.

A base de desenvolvimento utilizada nos testes iniciais emprega o kernel `6.18.45-current-rockchip`. A versão exata dos pacotes e do kernel poderá variar entre as imagens distribuídas.

Diferentemente da versão x86, que utiliza uma imagem live preparada para inicialização em computadores convencionais, este port precisa considerar o processo de boot, o armazenamento interno e as particularidades das placas RK322x.

## Compilação

Em breve.

---

# Limitações e bugs conhecidos

Esta versão ainda está em fase de testes e refinamento. Entre os pontos que merecem atenção estão:

- **Algumas TVs podem apresentar barras e bugs** Isso se deve devido a não suportar a resolução 640x480 que o emulador utiliza para oferecer melhor desempenho. Ainda não sei como melhorar isso.
- **Sem suporte a Bluetooth** futuramente, ainda que o hardware esteja presente, não tem um script de automação pronto para isso ainda.
- **Desempenho fraco em alguns jogos** Sim, o OpenMSX exige alguns recursos de hardware que superam a capacidade da caixinha, mas boa parte dos jogos e o BASIC rodam sem problemas.

Caso encontre algum problema, informe o modelo comercial da TV Box, o processador, a quantidade de memória e, se possível, a identificação da placa. Essas informações ajudam muito a compreender as diferenças entre os equipamentos.

---

# Hardware testado

A lista abaixo contém os equipamentos utilizados nos testes reais do projeto. Ela será atualizada conforme novos modelos forem validados.

| Fabricante / Modelo | Processador | Status | Observações |
|---|---|---|---|
| MXQ Pro 5G 4K | Rockchip RK3228A | Em testes | Armbian, Xfce e OpenMSX funcionando. Personalizações de inicialização e acabamento ainda em refinamento. |

**A presença de um modelo semelhante nesta tabela não garante compatibilidade com todas as revisões de placa vendidas sob o mesmo nome.**

Se você testar a imagem em outro equipamento da série RK322x, compartilhe os resultados para que possamos ampliar a lista de compatibilidade.


---

# Licença

O projeto GustoSX é distribuído sob a licença **GNU GPLv2**, conforme o projeto original.

Os componentes de terceiros, incluindo Linux, Armbian, OpenMSX e suas dependências, permanecem sujeitos às respectivas licenças e aos direitos de seus autores.

Este projeto é disponibilizado sem qualquer garantia. O usuário assume os riscos relacionados à instalação, modificação e utilização da distribuição.

Faça sempre backup dos seus dados e do firmware original. Não utilize ou armazene informações sigilosas, sensíveis ou críticas nesta distribuição.

---

# Considerações finais

A ideia do GustoSX continua sendo a mesma: aproveitar equipamentos que já temos, experimentar, aprender e trazer um pouco mais do universo MSX para o nosso dia a dia.

Agora, em vez de um netbook antigo, podemos ter uma pequena TV Box dedicada ao OpenMSX, ligada diretamente à televisão, trazendo mais uma forma de experimentar esse universo.

O projeto ainda está em desenvolvimento, e o feedback da comunidade será importante para melhorar a compatibilidade, corrigir problemas e descobrir até onde podemos chegar com essas pequenas placas RK322x.

Divirtam-se, **fudebas**!

---

# CHANGELOG

## [0.10.4] - Em desenvolvimento

- Port inicial do GustoSX para TV Boxes da série RK322x.
- Base Armbian com Debian 13 Trixie.
- Integração do ambiente gráfico Xfce.
- Compilação e execução do OpenMSX na arquitetura ARM.
- Inicialização automática do emulador.
- Personalizações iniciais de boot e identidade visual.
- Testes iniciais realizados em TV Box MXQ Pro 5G 4K com RK3228A.
