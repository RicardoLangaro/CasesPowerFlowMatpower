Descrição
-------------

O que é MATPOWER ?
Matpower é um pacote de arquivos .m Matlab® para resolver problemas de fluxo de energia e 
otimizá-los.Pretende ser uma ferramenta de simulação para pesquisadores e educadores
que seja fácil de usar e modificar. Matpower é projetado para oferecer o melhor desempenho
possível, mantendo o código simples de entender e modificar. O site oficial do Matpower
pode ser encontrado em:

https://matpower.org/

Matpower foi inicialmente desenvolvido por Ray D. Zimmerman, Carlos E. Murillo Sanchez e 
Deqiang Gan de PSerc1 na Universidade Cornell sob a direção de Robert J. Thomas. A 
necessidade inicial de fluxo de potência baseado em Matlab e potência ideal o código de 
fluxo nasceu dos requisitos computacionais do projeto PowerWeb2. Muitos outros contribuíram 
para o Matpower ao longo dos anos e continua a ser desenvolvido e mantido sob a direção 
de Ray Zimmerman. 
A partir da versão 6, o Matpower inclui uma estrutura para resolver problemas generalizados 
de programação de energia elétrica em estado estacionário. Esta estrutura é conhecida como
MOST, para Matpower Optimal Scheduling Tool.

https://matpower.org/docs/MOST-manual-1.0.2.pdf

O manual completo pode ser encontrado no site:

https://matpower.org/doc/manuals/

O que são esses estes arquivos disponibilizados?

São instâncias de fluxo de potência para redes de distribuição já conhecidas na literatura,
algumas transcritas por mim para o software MATPOWER.

Onde coloco esses arquivos?

Dentro da pasta raiz: %Matlab%/toolbox/matpower/data

Como simulo dentro do MATPOWER?

Por exemplo, o código a seguir executa um fluxo de energia no exemplo de 300 barramentos em
case300.m usando o algoritmo desacoplado rápido (versão XB), com impressão detalhada do 
progresso do algoritmo, mas suprimindo toda a saída.

>> mpopt = mpoption('pf.alg', 'FDXB', 'verbose', 2, 'out.all', 0);
>> results = runpf('case300', mpopt);

Para modificar uma estrutura de opções existente, por exemplo, para desligar a opção detalhada
e execute novamente com as opções restantes inalteradas, basta passar as opções existentes
como o primeiro argumento para mpoption.

>> mpopt = mpoption(mpopt, 'verbose', 0);
>> results = runpf('case300', mpopt);

Para fluxos de potência em redes de distribuição, o toolbox MATPOWER disponibiliza três modos
de simulação ( parâmetro 'pf.alg'), válido para redes radiais:

'PQSUM' { Power Summation (radial networks only)
'ISUM' { Current Summation (radial networks only)
'YSUM' { Admittance Summation (radial networks only)

>> mpopt = mpoption('pf.alg', 'ISUM', 'verbose', 3);
>> results = runpf('case10_grainger',mpopt)

Para acessar a ajuda:

>>help mpoption

