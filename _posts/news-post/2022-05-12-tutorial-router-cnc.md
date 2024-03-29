---
layout: blog_post
type: blog
teaserlatest: exemplo/full-printed.png
teaserlist: exemplo/full-printed.png
title: Orientações para operação de Router CNC
meta: "."
author: Dennison Siqueira
date: 12/05/2022
category: tutorial
---
<section class="tuto">
 <p>A router CNC é uma máquina capaz de fabricar peças a partir de modelos digitais em duas ou três dimensões, utilizando materiais como madeira, MDF, isopor, metais não ferrosos etc. Ela utiliza ferramentas de corte de diversos tipos para remover o material até que reste apenas o objeto desejado.</p>
 <p>Durante a fabricação da peça, o material removido se transforma em partículas que podem ser espalhar no ambiente. Para evitar esse inconveniente, a máquina conta com um equipamento auxiliar para aspiração do pó, de forma a conter a contaminação e manter baixos os níveis de toxicidade do ar.</p>
 <p>A router CNC não possui painel de controle, apenas botões para ligar e desligar e botão de parada de emergência. Todos os comandos de operação do equipamento são acessados pelo software supervisório que a acompanha (Mach3Mill).</p>
 <p>Para utilizar a router CNC é necessário seguir alguns passos, que serão detalhados a seguir, da preparação de um modelo digital à retirada de uma peça pronta.</p>

 <h2>Conteúdo</h2> 

 <ul>
  <li><a href="#modelagem">Modelagem 3D com Fusion 360</a></li>
  <li><a href="#gcode">Geração de Gcode para Router CNC</a></li>
  <li><a href="#setup">Preparação do equipamento</a></li>
  <li><a href="#corte">Executando o código</a></li>
  <li><a href="#final">Finalizando o trabalho</a></li>
 </ul>
 
 <h2 id="modelagem">Modelagem 3D com Fusion 360</h2>

 <p>A peça a ser fabricada em uma router CNC precisa ser um desenho digital, vetorizado, em formato DXF ou um modelo 3D em formato STL. Softwares como Fusion 360, AutoCAD, SolidWorks, CorelDraw (somente 2D), Adobe Illustrator (somente 2D) são capazes de gerar os desenhos adequados.</p>
 <p>Neste trabalho utilizaremos o software Autodesk Fusion 360, disponível no FabLab. O Fusion 360 nos permite criar um modelo 3D e possui ferramentas para geração do código compatível com a router CNC.</p>
 <p>Abra o software Fusion 360.</p>
 <p>Verifique se o espaço de trabalho DESING está ativo.</p>
 
 <h3>Crie um desenho 2D</h3>
 <p>Comece a desenhar a letra inicial do seu nome, que se tornará a base do modelo 3D, no plano XY.</p>
 
 <ol>
  <div class="row">
   <div class="col-md-6">
    <li>Clique em “Solid> Create> Create Sketch”   .</li>
    <li>Selecione o plano XY para desenhar.</li>
    <p><smal>Quando você seleciona o plano, entra na guia de contexto “Sketch”, que contém as ferramentas de Sketch usadas com mais frequência.</smal></p>
   </div>
   <div class="col-md-6">
    <img src="{{ site.url }}/img/blog/tutorial-router/create-sketch.png">
   </div>
  </div>
  
  <div class="row">
   <div class="col-md-6">
    <img src="{{ site.url }}/img/blog/tutorial-router/create-text.png">
   </div>
   <div class="col-md-6">
    <li>Clique em “Sketch> Create> Text”  </li>
    <li>Passe o mouse sobre a origem do esboço. O cursor se encaixa automaticamente neste local.</li>
    <li>Clique na origem e depois em outro ponto para desenhar uma caixa de texto retangular.</li>
     <img src="{{ site.url }}/img/blog/tutorial-router/caixa-de-texto.png">
   </div>
  </div>

  <div class="row">
   <div class="col-md-6">
    <li>Selecione as opções desejadas na caixa de diálogo “TEXT”. Digite seu texto; defina a altura da caixa de texto como 100mm (essa altura não corresponde à altura da letra digitada, mas à altura da caixa de texto que pode ser um pouco maior); escolha uma fonte.</li>
    <li>Clique em “OK”.</li>
    <p><strong>Dica:</strong> Clique na casinha ao lado do View Cube para visualizar o esboço em seu tamanho e orientação originais. </p>
     <img src="{{ site.url }}/img/blog/tutorial-router/view-cube.png">
   </div>
   <div class="col-md-6">
    <img src="{{ site.url }}/img/blog/tutorial-router/editando-text.png">
   </div>
  </div>
 </ol>

<h3>Transformando um sketch em um modelo 3D</h3>
<p>Faça a extrusão da letra que você acabou de criar, 15 mm, para converter seu perfil de esboço 2D em geometria 3D.</p>

 <ol>
    <div class="row">
   <div class="col-md-6">
       <img src="{{ site.url }}/img/blog/tutorial-router/create-extrude.png">
   </div>
   <div class="col-md-6">
    <li>Clique em “Solid > Crate> Extrude”  . Isso exibe a caixa de diálogo “EXTRUDE”.</li>
   </div>
  </div>

  <div class="row">
   <div class="col-md-6">
    <li>Selecione a letra como o perfil que você deseja extrudar. </li>
    <li>Arraste a seta azul para cima 15 mm para definir a profundidade da letra.</li>
    <p><strong>Dica:</strong> Se você não pode arrastar o mouse para exatamente 15 mm, digite “15” no campo “Distance” e pressione “Enter”.</p>
    <li>Clique em “OK” na caixa de diálogo “EXTRUDE”.</li>
   </div>
   <div class="col-md-6">
    <img src="{{ site.url }}/img/blog/tutorial-router/editando-extrude.png">
   </div>
  </div>
 </ol>     
 <img src="{{ site.url }}/img/blog/tutorial-router/extrude-editado.png">
 
<h2 id="gcode">Geração de Gcode para Router CNC</h2>
<h3>Ambiente de trabalho MANUFACTURE (CAM)</h3>
<p>O ambiente de trabalho MANUFACTURE do Fusion 360 contém ferramentas CAM para ajudá-lo a gerar caminhos de ferramenta, programar máquinas CNC e dar vida a seus projetos.</p>
<p>Para ir para o ambiente de trabalho MANUFACTURE, selecione “MANUFACTURE” na lista suspensa.</p>

<h3>Crie um Setup para operação de fresagem</h3>
 
 <ol>
  <li>Na barra de ferramentas “MANUFACTURE”, clique em “Setup > New Setup”  .</li>
  <p>A caixa de diálogo “Setup” é exibida.</p>
  <li>Na caixa de diálogo “Setup”, selecione o tipo de operação (Operation Type) “Milling”.</li>
  <li>Preencha a área “Work Coordinate System (WCS)”, para especificar a orientação e a origem do sistema de coordenadas da peça de trabalho.</li>
  <li>Preencha a área “Model”, para especificar qual modelo está incluído no Setup. Por padrão, todos os modelos na tela são selecionados automaticamente.</li>
  <li>Preencha a guia “Stock”, para definir o tamanho e a forma da peça de trabalho. Mantenha as configurações padrão exceto o campo “Stock Top Offset” que deve ser modificado para “0mm”.</li>
  <li>Clique em “OK”.</li>
 </ol>
 
 <h3>Configurando um corte de contorno 2D</h3>
 <h4>Abra a biblioteca de ferramentas</h4>
 
 <ol>
  <li>Na barra de ferramentas “MANUFACTURE”, guia “Milling”, selecione “2D > 2D Contour”   .</li>
  <p>A paleta de comandos “2D Contour” é aberta.</p>
  <li>Na guia “Tool”    , clique em “Select”.</li>
  <p>Isso abre a biblioteca de ferramentas.</p>
 </ol>
 
 <h4>Crie e selecione uma nova ferramenta de corte</h4>
 
 <ol>
  <li>Clique no botão “New Mill Tool”   .</li>
  <li>Na guia “Cutter”, na lista suspensa “Type”, selecione a opção ”Flat end mill”.</li>
  <li>No grupo “Geomety”, defina o Diâmetro para 4mm.</li>
  <li>Para poder cortar toda a altura da peça, aumente o comprimento da fresa para 15 mm.</li>
  <li>Clique em “OK” para criar a ferramenta.</li>
  <li>Selecione a nova ferramenta e clique em “OK “para fechar a caixa de diálogo.</li>
 </ol>
 
 <h4>Defina a velocidade de rotação e avanço</h4>

 <p>No grupo “Feed & Speed”, defina a velocidade do eixo da ferramenta (Spindle Speed) para 15000 RPM e o avanço de corte (Cutting Feedrate) para 800mm/min.</p>
 <p><strong>Importante:</strong> Defina os parâmetros de velocidade e avanço com base nas recomendações dos fornecedores de ferramentas e no tipo de material.</p>

<h4>Selecione o contorno a ser usinado</h4>

 <ol>
  <li>Clique na guia “Geometry”   .</li>
  <li>Verifique se o botão “Contourn selection” está ativo para que você possa selecionar a aresta externa da geometria da peça para rodar a ferramenta.</li>
  <li>Mova o ponteiro do mouse sobre a borda inferior.</li>
  <li>Quando a borda se destacar, clique nela. A aresta é selecionada automaticamente como uma corrente.</li>
  <p>Observe a linha azul ao redor da peça. A seta vermelha deve estar do lado de fora, apontando no sentido horário (CW) ao redor da peça.</p>
  <p><strong>Dica:</strong> Você pode reverter a direção de uma aresta selecionada clicando na seta vermelha.</p>
 </ol>
 
<h4>Crie “Tabs” para a peça não sair voando</h4>

<p>Você pode adicionar Tabs ao caminho da ferramenta 2D Contourn para prender a peça com segurança enquanto o material é usinado. As Tabs são muito úteis ao cortar plástico fino ou madeira.</p>
<p>Ative a caixa de seleção “Tabs” e defina os parâmetros conforme a imagem abaixo.</p>

<p>Em “Tab Positions” use o cursor para selecionar pontos ao longo do caminho do contorno para os locais das Tabs.</p>
<p>Dica: As tabs podem ser removidas manualmente com o auxílio de uma lima.</p>

<h4>Configure as alturas</h4>
 
 <ol>
  <li>Clique na guia “Heights”   . Uma prévia das alturas é mostrada.</li>
  <p>As alturas são codificadas por cores e rotuladas para facilitar a identificação.</p>
  <li>O menu suspenso “Bottom Height” deve ser definido como “Model bottom”.</li>
  <li>Para garantir que a peça será cortada até o final, defina o deslocamento (Offset) da altura inferior como “-1mm”. Observe que o plano azul escuro, a altura inferior, se move para baixo.</li>
 </ol>
 
 <h4>Defina a profundidade de corte</h4>
 
 <ol>
  <li>Clique na guia “Passes”   .</li>
  <p>Este grupo de configurações controla como o caminho da ferramenta de contorno 2D é calculado. Para cortar a peça, o caminho da ferramenta é gerado em vários níveis Z, começando da parte superior do material e descendo em etapas de 3mm até a parte inferior do modelo.</p>
  <li>Ative a opção “Multiple Depths”.</li>
  <li>Defina o desbaste máximo (Maximum Roughing Stepdown) para 3mm.</li>
  <li>Clique em “OK” para iniciar o cálculo.</li>
 </ol>

<h3>Simulação da usinagem</h3>

<p>O recurso “Simulate” permite verificar se o caminho da ferramenta gerado é o pretendido. A simulação é iniciada selecionando as operações de interesse no Browser e, em seguida, clicando na opção “Actions > Simulate”  .</p>
<p>As operações são simuladas na ordem original conforme aparecem no Browser.</p>
<p>Depois de iniciada, a caixa de diálogo “Simulate” é aberta e o player é exibido na parte inferior da tela. </p>
<p>Você pode habilitar as caixas de seleção para mostrar o material dentro da simulação. Também é possível mostrar a ferramenta, o caminho e o material individualmente ou em conjunto, ativando ou desativando as respectivas caixas de seleção “Tool”, “Toolpath” e “Stock”.</p>
<p>Para a iniciar a animação da ferramenta, clique no botão “Start” no Simulador.
A animação pode ser pausada e reproduzida clicando no botão “Pause” e “Start”, respectivamente.
Para encerrar a simulação clique em “Close” na caixa de diálogo.</p>

<h3>Pós Processamento</h3>

<p>OK, você projetou seu primeiro modelo e concluiu seus primeiros caminhos de ferramenta. Agora você está se perguntando como fazer a router CNC cortar a peça. Para isso, você precisa de um pós-processador.</p>

<p>Um pós-processador é um tradutor que converte a imagem do caminho da ferramenta que você vê na tela para a linguagem que a router CNC entende. 
Na maioria dos casos, essa linguagem é o código G, embora algumas máquinas possam usar um formato diferente. Vamos nos referir a ele como "G code".
Para gerar o G code, selecione o Setup criado no Browser. Depois de selecionar os caminhos da ferramenta, clique em “Actions> Post Process”  .</p>

<p>Na caixa de diálogo “Post Process”, selecione o pós-processador correto da máquina. Puxe a lista abaixo da seção Post Configuration da caixa de diálogo e role até a opção “CNC Router Parts(Mach3Mill)”. </p>

<p>Clique no botão “Post” para realizar o pós-processamento.
Na janela “Post Process”, selecione uma pasta para salvar o G code, dê um nome ao arquivo e clique em “Salvar”.
Um arquivo com a extensão *.tap foi gerado na pasta selecionada. Transfira o arquivo para um pendrive e leve-o até o controlador da router CNC.</p>
 
<h2 id="setup">Preparação do equipamento</h2>

<p>Antes de iniciar a execução do projeto, são necessários alguns passos para preparar a máquina. Esse procedimento ocorre em 13 etapas, da seguinte forma: </p>
 
 <ol>
  <li>Conecte a pinça de 4mm à porca do spindle e insira a fresa de 4mm.</li>
  <li>Com as ferramentas adequadas, fixe o conjunto na extremidade do spindle; </li>
  <li>Posicione a mangueira do exaustor e fixe-a; </li>
  <li>Posicione o material a ser usinado sobre a mesa; </li>
  <p><strong>Importante:</strong> Utilize um material de sacrifício entre a peça e a mesa. Uma chapa de MDF de 6mm é o suficiente.</p>
  <li>Fixe o com os recursos necessários (parafusos, sargentos, presilhas); </li>
  <li>No computador da máquina, abra o Mach3Mill; </li>
  <li>Gire o botão On/Off, para ligar o sistema; </li>
  <li>Clique no botão “Reset”; </li>
  <li>Utilizando as setas do teclado (eixo XY), posicione a fresa na origem do material (canto inferior esquerdo); </li>
  <li>Utilizando as teclas “PageUp” e “PageDown” (eixo Z), toque a ponta da fresa na superfície do material; </li>
  <p>Dica: A tecla Shift permite o movimento em velocidade maior. Cuidado ao utilizar esta função.</p>
  <li>Na parte superior da tela, zere as coordenadas X, Y e Z; </li>
  <li>Afaste a fresa do material por segurança. Cerca de dois centímetros é o bastante.</li>
  <li>Ligue o exaustor.</li>
 </ol>

 <h2 id="corte">Executando o código</h2>

 <p>Antes de executar o trabalho, o operador (e demais pessoas no ambiente) deve colocar os EPI’s obrigatórios (óculos de proteção, abafador concha e máscara para poeiras). <p/>
 <p>Com o desenho configurado, a máquina ajustada e o operador seguro, o trabalho pode ser iniciado.Esse procedimento ocorre em 5 etapas, da seguinte forma: </p>
 
 <ol>
  <li>No canto superior esquerdo da tela, clique em “Load Code”; </li>
  <li>Na janela que foi aberta, selecione seu arquivo e clique em “Abrir”;</li>
  <li>Verifique se o arquivo carregado está correto, através da posição e dos valores de “spindle”, “Z” e etc; </li>
  <li>Ligue o aspirador; </li>
  <li>Clique em “CycleStart”. </li>
 </ol>
 
 <p>Supervisione o funcionamento da máquina até o final do processo. Nunca a deixe trabalhando sozinha. Fique atento a possíveis erros durante a fabricação da sua peça. Caso observe algo de errado interrompa o corte pressionando o botão de emergência.</p>

 <h2 id="final">Finalizando o trabalho</h2>

 <p>Após todos os trabalhos serem executados, a máquina movimentará a fresa até a origem, informando que encerrou sua atividade. Para encerrar seu projeto, devem ser seguidas 6 etapas, da seguinte forma: </p>
 <ol>
  <li>Pelo teclado, movimente o bico para fora da área trabalhada; </li>
  <li>Pressione o “Botão de Emergência” para evitar acidentes; </li>
  <li>Remova a fixação da placa e retire-a da mesa; </li>
  <li>Com auxílio de ferramentas, remova as pontes (tabs) que prendem a peça à placa; </li>
  <li>Gire o botão “Liga Máquina” para desligar o sistema; </li>
  <li>No computador, feche o Mach3Mill.</li>
 </ol>
 
