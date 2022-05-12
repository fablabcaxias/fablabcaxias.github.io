Orientações para operação de Router CNC com Fusion 360

Sumário
1. Introdução	1
2. Modelagem 3D com Fusion 360
3. Geração de Gcode para Router CNC
4. Preparação do equipamento
5. Executando o código
6. Finalizando o trabalho

1. Introdução
A router CNC é uma máquina capaz de fabricar peças a partir de modelos digitais em duas ou três dimensões, utilizando materiais como madeira, MDF, isopor, metais não ferrosos etc. Ela utiliza ferramentas de corte de diversos tipos para remover o material até que reste apenas o objeto desejado.
Durante a fabricação da peça, o material removido se transforma em partículas que podem ser espalhar no ambiente. Para evitar esse inconveniente, a máquina conta com um equipamento auxiliar para aspiração do pó, de forma a conter a contaminação e manter baixos os níveis de toxicidade do ar.
A router CNC não possui painel de controle, apenas botões para ligar e desligar e botão de parada de emergência. Todos os comandos de operação do equipamento são acessados pelo software supervisório que a acompanha (Mach3Mill).
Para utilizar a router CNC é necessário seguir alguns passos, que serão detalhados a seguir, da preparação de um modelo digital à retirada de uma peça pronta.
2. Modelagem 3D com Fusion 360
A peça a ser fabricada em uma router CNC precisa ser um desenho digital, vetorizado, em formato DXF ou um modelo 3D em formato STL. Softwares como Fusion 360, AutoCAD, SolidWorks, CorelDraw (somente 2D), Adobe Illustrator (somente 2D) são capazes de gerar os desenhos adequados.
Neste trabalho utilizaremos o software Autodesk Fusion 360, disponível no FabLab. O Fusion 360 nos permite criar um modelo 3D e possui ferramentas para geração do código compatível com a router CNC.
Abra o software Fusion 360.
Verifique se o espaço de trabalho DESING está ativo.
 

2.1 Crie um desenho 2D
Comece a desenhar a letra inicial do seu nome, que se tornará a base do modelo 3D, no plano XY.
a)	Clique em “Solid> Create> Create Sketch”   .

b)	Selecione o plano XY para desenhar.

Quando você seleciona o plano, entra na guia de contexto “Sketch”, que contém as ferramentas de Sketch usadas com mais frequência. 

c)	Clique em “Sketch> Create> Text”  

d)	Passe o mouse sobre a origem do esboço. O cursor se encaixa automaticamente neste local.

 


e)	Clique uma vez para posicionar o texto.

f)	Selecione as opções desejadas na caixa de diálogo “TEXT”. Digite seu texto; defina a altura da caixa de texto como 100mm (essa altura não corresponde à altura da letra digitada, mas à altura da caixa de texto que pode ser um pouco maior); escolha uma fonte.

g)	Clique em “OK”.
Dica: Clique na casinha ao lado do View Cube para visualizar o esboço em seu tamanho e orientação originais. 
 
2.2 Transformando um sketch em um modelo 3D
Faça a extrusão da letra que você acabou de criar, 15 mm, para converter seu perfil de esboço 2D em geometria 3D.
a)	Clique em “Solid > Crate> Extrude”  . Isso exibe a caixa de diálogo “EXTRUDE”.

b)	Selecione a letra como o perfil que você deseja extrudar. 

c)	Arraste a seta azul para cima 15 mm para definir a profundidade da letra.
Dica: Se você não pode arrastar o mouse para exatamente 15 mm, digite “15” no campo “Distance” e pressione “Enter”.
d)	Clique em “OK” na caixa de diálogo “EXTRUDE”.
3. Geração de Gcode para Router CNC
3.1 Ambiente de trabalho MANUFACTURE (CAM)
O ambiente de trabalho MANUFACTURE do Fusion 360 contém ferramentas CAM para ajudá-lo a gerar caminhos de ferramenta, programar máquinas CNC e dar vida a seus projetos.
Para ir para o ambiente de trabalho MANUFACTURE, selecione “MANUFACTURE” na lista suspensa.
3.2 Crie um Setup para operação de fresagem.
a)	Na barra de ferramentas “MANUFACTURE”, clique em “Setup > New Setup”  .

A caixa de diálogo “Setup” é exibida.

b)	Na caixa de diálogo “Setup”, selecione o tipo de operação (Operation Type) “Milling”.

c)	Preencha a área “Work Coordinate System (WCS)”, para especificar a orientação e a origem do sistema de coordenadas da peça de trabalho.

d)	Preencha a área “Model”, para especificar qual modelo está incluído no Setup. Por padrão, todos os modelos na tela são selecionados automaticamente.

e)	Preencha a guia “Stock”, para definir o tamanho e a forma da peça de trabalho. Mantenha as configurações padrão exceto o campo “Stock Top Offset” que deve ser modificado para “0mm”.

f)	Clique em “OK”.
3.3 Configurando um corte de contorno 2D
3.3.1 Abra a biblioteca de ferramentas
a)	Na barra de ferramentas “MANUFACTURE”, guia “Milling”, selecione “2D > 2D Contour”   .

A paleta de comandos “2D Contour” é aberta.
b)	Na guia “Tool”    , clique em “Select”.

Isso abre a biblioteca de ferramentas.
3.3.2 Crie e selecione uma nova ferramenta de corte.
a)	Clique no botão “New Mill Tool”   .

b)	Na guia “Cutter”, na lista suspensa “Type”, selecione a opção ”Flat end mill”.

c)	No grupo “Geomety”, defina o Diâmetro para 4mm.

d)	Para poder cortar toda a altura da peça, aumente o comprimento da fresa para 15 mm.

e)	Clique em “OK” para criar a ferramenta.

f)	Selecione a nova ferramenta e clique em “OK “para fechar a caixa de diálogo.
3.3.3 Defina a velocidade de rotação e avanço
No grupo “Feed & Speed”, defina a velocidade do eixo da ferramenta (Spindle Speed) para 15000 RPM e o avanço de corte (Cutting Feedrate) para 800mm/min.
Importante: Defina os parâmetros de velocidade e avanço com base nas recomendações dos fornecedores de ferramentas e no tipo de material.
3.3.4 Selecione o contorno a ser usinado
a)	Clique na guia “Geometry”   .

b)	Verifique se o botão “Contourn selection” está ativo para que você possa selecionar a aresta externa da geometria da peça para rodar a ferramenta.

c)	Mova o ponteiro do mouse sobre a borda inferior.

d)	Quando a borda se destacar, clique nela. A aresta é selecionada automaticamente como uma corrente.

Observe a linha azul ao redor da peça.

A seta vermelha deve estar do lado de fora, apontando no sentido horário (CW) ao redor da peça.

Dica: Você pode reverter a direção de uma aresta selecionada clicando na seta vermelha.
3.3.5 Crie “Tabs” para a peça não sair voando
Você pode adicionar Tabs ao caminho da ferramenta 2D Contourn para prender a peça com segurança enquanto o material é usinado. As Tabs são muito úteis ao cortar plástico fino ou madeira.
Ative a caixa de seleção “Tabs” e defina os parâmetros conforme a imagem abaixo:
 
Em “Tab Positions” use o cursor para selecionar pontos ao longo do caminho do contorno para os locais das Tabs.
Dica: As tabs podem ser removidas manualmente com o auxílio de uma lima.
3.3.6 Configure as alturas
a)	Clique na guia “Heights”   . Uma prévia das alturas é mostrada.
As alturas são codificadas por cores e rotuladas para facilitar a identificação.
b)	O menu suspenso “Bottom Height” deve ser definido como “Model bottom”.
c)	Para garantir que a peça será cortada até o final, defina o deslocamento (Offset) da altura inferior como “-1mm”. Observe que o plano azul escuro, a altura inferior, se move para baixo.
3.3.7 Defina a profundidade de corte
a)	Clique na guia “Passes”   . Este grupo de configurações controla como o caminho da ferramenta de contorno 2D é calculado. Para cortar a peça, o caminho da ferramenta é gerado em vários níveis Z, começando da parte superior do material e descendo em etapas de 3mm até a parte inferior do modelo.
b)	Ative a opção “Multiple Depths”.
c)	Defina o desbaste máximo (Maximum Roughing Stepdown) para 3mm.
d)	Clique em “OK” para iniciar o cálculo.
3.4 Simulação da usinagem
O recurso “Simulate” permite verificar se o caminho da ferramenta gerado é o pretendido.
A simulação é iniciada selecionando as operações de interesse no Browser e, em seguida, clicando na opção “Actions > Simulate”  .
 As operações são simuladas na ordem original conforme aparecem no Browser. Depois de iniciada, a caixa de diálogo “Simulate” é aberta e o player é exibido na parte inferior da tela. 
Você pode habilitar as caixas de seleção para mostrar o material dentro da simulação. Também é possível mostrar a ferramenta, o caminho e o material individualmente ou em conjunto, ativando ou desativando as respectivas caixas de seleção “Tool”, “Toolpath” e “Stock”.
Para a iniciar a animação da ferramenta, clique no botão “Start” no Simulador. A animação pode ser pausada e reproduzida clicando no botão “Pause” e “Start”, respectivamente.
Para encerrar a simulação clique em “Close” na caixa de diálogo.
3.5 Pós Processamento
OK, você projetou seu primeiro modelo e concluiu seus primeiros caminhos de ferramenta. Agora você está se perguntando como fazer a router CNC cortar a peça. Para isso, você precisa de um pós-processador.
Um pós-processador é um tradutor que converte a imagem do caminho da ferramenta que você vê na tela para a linguagem que a router CNC entende. Na maioria dos casos, essa linguagem é o código G, embora algumas máquinas possam usar um formato diferente. Vamos nos referir a ele como "G code".
Para gerar o G code, selecione o Setup criado no Browser. Depois de selecionar os caminhos da ferramenta, clique em “Actions> Post Process”  .
Na caixa de diálogo “Post Process”, selecione o pós-processador correto da máquina. Puxe a lista abaixo da seção Post Configuration da caixa de diálogo e role até a opção “CNC Router Parts(Mach3Mill)”. 
Clique no botão “Post” para realizar o pós-processamento.
Na janela “Post Process”, selecione uma pasta para salvar o G code, dê um nome ao arquivo e clique em “Salvar”.
Um arquivo com a extensão *.tap foi gerado na pasta selecionada. Transfira o arquivo para um pendrive e leve-o até o controlador da router CNC.
4. Preparação do equipamento
Antes de iniciar a execução do projeto, são necessários alguns passos para preparar a máquina. Esse procedimento ocorre em 13 etapas, da seguinte forma: 
a)	Conecte a pinça de 4mm à porca do spindle e insira a fresa de 4mm.
b)	Com as ferramentas adequadas, fixe o conjunto na extremidade do spindle; 
c)	Posicione a mangueira do exaustor e fixe-a; 
d)	Posicione o material a ser usinado sobre a mesa; 
Importante: Utilize um material de sacrifício entre a peça e a mesa. Uma chapa de MDF de 6mm é o suficiente.
e)	Fixe o com os recursos necessários (parafusos, sargentos, presilhas); 
f)	No computador da máquina, abra o Mach3Mill; 
g)	Gire o botão On/Off, para ligar o sistema; 
h)	Clique no botão “Reset”; 
i)	Utilizando as setas do teclado (eixo XY), posicione a fresa na origem do material (canto inferior esquerdo); 
j)	Utilizando as teclas “PageUp” e “PageDown” (eixo Z), toque a ponta da fresa na superfície do material; 
Dica: A tecla Shift permite o movimento em velocidade maior. Cuidado ao utilizar esta função.
k)	Na parte superior da tela, zere as coordenadas X, Y e Z; 
l)	Afaste a fresa do material por segurança. Cerca de dois centímetros é o bastante.
m)	Ligue o exaustor.

5. Executando o código
Antes de executar o trabalho, o operador (e demais pessoas no ambiente) deve colocar os EPI’s obrigatórios (óculos de proteção, abafador concha e máscara para poeiras). Com o desenho configurado, a máquina ajustada e o operador seguro, o trabalho pode ser iniciado.
Esse procedimento ocorre em 5 etapas, da seguinte forma: 
a) No canto superior esquerdo da tela, clique em “Load Code”; 
b) Na janela que foi aberta, selecione seu arquivo e clique em “Abrir”;
 c) Verifique se o arquivo carregado está correto, através da posição e dos valores de “spindle”, “Z” e etc; 
d) Ligue o aspirador; 
e) Clique em “CycleStart”. 
Supervisione o funcionamento da máquina até o final do processo. Nunca a deixe trabalhando sozinha. Fique atento a possíveis erros durante a fabricação da sua peça. Caso observe algo de errado interrompa o corte pressionando o botão de emergência.
6. Finalizando o trabalho
Após todos os trabalhos serem executados, a máquina movimentará a fresa até a origem, informando que encerrou sua atividade. Para encerrar seu projeto, devem ser seguidas 6 etapas, da seguinte forma: 
a) Pelo teclado, movimente o bico para fora da área trabalhada; 
b) Pressione o “Botão de Emergência” para evitar acidentes; 
c) Remova a fixação da placa e retire-a da mesa; 
d) Com auxílio de ferramentas, remova as pontes (tabs) que prendem a peça à placa; 
e) Gire o botão “Liga Máquina” para desligar o sistema; 
f) No computador, feche o Mach3Mill.

