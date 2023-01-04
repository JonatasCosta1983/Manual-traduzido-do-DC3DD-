# Manual-traduzido-do-DC3DD
O DC3DD é uma aplicação personalizada para o universo da forense digital, essa é uma tradução livre do inglês para português brasil para facilitar o seu uso. 
Comandos do usuário DC3DD(1) DC3DD(1) 

NOME dc3dd - converte e copia um arquivo 

DESCRIÇÃO ------ uso: ------ 

          dc3dd [OPÇÃO 1] [OPÇÃO 2] ... [OPÇÃO N] 
 
           *ou* 
 
           dc3dd [OPÇÃO DE AJUDA] 
 
           onde cada OPÇÃO é selecionada nas opções básicas ou avançadas listadas abaixo, ou OPÇÃO DE AJUDA é selecionada nas opções de ajuda 
           listado abaixo. 
    
    -------------- opções básicas: -------------- 
 
    if=DISPOSITIVO ou ARQUIVO 
           Leia a entrada de um dispositivo ou arquivo (consulte a observação nº 1 abaixo para saber como ler a partir da entrada padrão). Esta opção só pode ser usada uma vez e 
           não pode ser combinado com ifs=, pat= ou tpat=. 
 
    ifs=BASE.FMT 
           Lê a entrada de um conjunto de arquivos com o nome base BASE e extensões de nome de arquivo sequencial de acordo com o especificador de formato FMT (consulte 
           nota #4 abaixo para saber como especificar FMT). Esta opção só pode ser usada uma vez e não pode ser combinada com if=, pat= ou tpat=. 
 
    of=ARQUIVO ou DISPOSITIVO 
           Escreva a saída em um arquivo ou dispositivo (consulte a nota nº 2 abaixo para saber como gravar na saída padrão). Esta opção pode ser usada mais de uma vez 
           (consulte a nota nº 3 abaixo para saber como gerar várias saídas). 
 
    hof=ARQUIVO ou DISPOSITIVO 
           Grave a saída em um arquivo ou dispositivo, faça o hash dos bytes de saída e verifique comparando o(s) hash(es) de saída com o(s) hash(es) de entrada. Esta 
           opção pode ser usada mais de uma vez (consulte a nota nº 3 abaixo para saber como gerar várias saídas). 
 
    ofs=BASE.FMT 
           Grave a saída em um conjunto de arquivos com o nome base BASE e extensões de nome de arquivo sequencial geradas a partir do especificador de formato FMT (consulte 
           nota #4 abaixo para saber como especificar FMT). Esta opção pode ser usada mais de uma vez (consulte a nota nº 3 abaixo para saber como gerar múltiplas saídas). 
           coloca). Especifique o tamanho máximo de cada arquivo no conjunto usando ofsz=. 
 

    hofs=BASE.FMT Grave a saída em um conjunto de arquivos com o nome base BASE e extensões de nome de arquivo gerados sequencialmente a partir do especificador de formato FMT (consulte a nota #4 abaixo para saber como especificar FMT). Faça um hash dos arquivos de saída e verifique comparando o(s) hash(es) de saída com o(s) hash(es) de entrada. Esta opção pode ser usada mais de uma vez (consulte a nota nº 3 abaixo para saber como gerar várias saídas). Especifique o tamanho máximo de cada arquivo no conjunto usando ofsz=. 

    ofsz=BYTES 
           Defina o tamanho máximo de cada arquivo nos conjuntos de arquivos especificados usando ofs= ou hofs= para BYTES (consulte a nota nº 5 abaixo). Um valor padrão 
           para esta opção pode ser definido em tempo de compilação usando -DDEFAULT_OUTPUT_FILE_SIZE seguido pelo valor desejado em BYTES. 
 
    hash=ALGORITMO 
           Calcule um hash ALGORITHM da entrada e também de quaisquer saídas especificadas usando hof=, hofs= ou fhod=, onde ALGORITHM é um dos 
           md5, sha1, sha256 ou sha512. Esta opção pode ser usada uma vez para cada ALGORITMO suportado. Alternativamente, o hashing pode ser ativado em 
           tempo de compilação usando um ou mais de -DDEFAULT_HASH_MD5,-DDEFAULT_HASH_SHA1, -DDEFAULT_HASH_SHA256 e -DDEFAULT_HASH_SHA512. 
 
    log=ARQUIVO 
           Registre estatísticas de E/S, diagnósticos e hashes totais de entrada e saída em ARQUIVO. Se hlog= não for especificado, hashes por partes de vários 
           entrada e saída de arquivo simples também são registradas em ARQUIVO. Esta opção pode ser usada mais de uma vez para gerar vários logs. 
 
    hlog=ARQUIVO 
           Registre o total de hashes e os hashes por partes em FILE. Esta opção pode ser usada mais de uma vez para gerar vários logs. 
 
    mlog=ARQUIVO 
           Crie log de hash que seja mais fácil para a máquina ler 
 
    ----------------- opções avançadas: ----------------- 
 
    fhod=DISPOSITIVO 
           O mesmo que hof=DEVICE, com hash adicional de todo o DEVICE de saída. Esta opção pode ser usada mais de uma vez (veja nota #3 
           abaixo para saber como gerar várias saídas). 
 
    rec=desligado 
           Por padrão, zeros são gravados na(s) saída(s) no lugar de setores defeituosos quando a entrada é um dispositivo. Use esta opção para fazer com que o 
           programa para sair quando um setor defeituoso é encontrado.
            
    wipe=DISPOSITIVO 
           Limpe DEVICE escrevendo zeros (padrão) ou um padrão especificado por pat= ou tpat=. 
 
    hwipe=DISPOSITIVO 
           Limpe DEVICE escrevendo zeros (padrão) ou um padrão especificado por pat= ou tpat=. Verifique o DEVICE depois de escrevê-lo, fazendo hash e 
           comparando o(s) hash(es) com o(s) hash(es) de entrada. 
 
    pat=HEX 
           Use o padrão como entrada, escrevendo HEX em cada byte da saída. Esta opção só pode ser usada uma vez e não pode ser combinada com if=, 
           ifs=, ou tpat=. 
 
    tpat=TEXTO 
           Use o padrão de texto como entrada, escrevendo a string TEXT repetidamente na saída. Esta opção só pode ser usada uma vez e não pode ser combinada 
           combinado com if=, ifs= ou pat=. 
 
    cnt=SETORES 
           Leia apenas os setores de entrada de SECTORS. Deve ser usado com pat= ou tpat= se não estiver usando o padrão com wipe= ou hwipe= para limpar um dispositivo. 
 
    iskip=SETORES 
           Ignore os setores SECTORS no início do dispositivo de entrada ou arquivo. 
 
    oskip=SETORES 
           Ignore os setores SECTORS no início do arquivo de saída. A especificação de oskip= define automaticamente app=on. 
 
    app=on Não substitua um arquivo de saída especificado com of= se ele já existir, anexando a saída em vez disso. 
 
    ssz=BYTES 
           Use BYTES incondicionalmente (veja a nota nº 5 abaixo) bytes para o tamanho do setor. Se ssz= não for especificado, o tamanho do setor é determinado por sondagem 
           o dispositivo; se a investigação falhar ou o destino não for um dispositivo, um tamanho de setor de 512 bytes será assumido. 
            
           bufsz=BYTES 
           Defina o tamanho dos buffers de bytes internos para BYTES (consulte a nota nº 5 abaixo). Isso efetivamente define o número máximo de bytes que podem 
           ser lido de cada vez a partir da entrada. BYTES deve ser um múltiplo do tamanho do setor. Use esta opção para ajustar o desempenho. 
 
    verbo=on 
           Ative o relatório detalhado, onde os setores de entrada/saída são relatados para cada arquivo em conjuntos de arquivos especificados usando ifs=, ofs= ou hofs=. 
           Como alternativa, relatórios detalhados podem ser ativados no tempo de compilação usando -DDEFAULT_VERBOSE_REPORTING. 
 
    nwspc=ligado 
           Ative o relatório compacto, onde o uso de espaço em branco para dividir a saída de log em seções lógicas é suprimido. Alternativamente, 
           relatórios compactos podem ser ativados em tempo de compilação usando -DDEFAULT_COMPACT_REPORTING. 
 
    b10=on Ativa o relatório de base 10 bytes, onde a exibição de progresso relata 1.000 bytes em vez de 1.024 bytes como 1 KB. Alternativamente, base 
           O relatório de 10 bytes pode ser ativado em tempo de compilação usando -DDEFAULT_BASE_TEN_BYTES_REPORTING. 
 
    saída corrompida=ligada 
           Para fins de teste de verificação e demonstração, corrompa o(s) arquivo(s) de saída com bytes extras para garantir uma incompatibilidade de hash. 
           ------------- opções de ajuda: ------------- 
 
    --help exibe esta ajuda e sai 
 
    --versão 
           informações de versão de saída e saída 
 
    --bandeiras 
           exibir sinalizadores de tempo de compilação e sair 
 
    ------ notas: ------ 
 
    1. Para ler de stdin, não especifique if=, ifs=, pat= ou tpat=. 2. Para gravar em stdout, não especifique of=, hof=, ofs=, hofs=, fhod=, 
 
           limpe= ou hwipe=. 
 
    3. Para gravar em várias saídas, especifique mais de um of=, hof=, ofs=, 
 
           hofs=, ou fhod=, em qualquer combinação. 
 
    4. FMT é um padrão para uma sequência de extensões de arquivo que podem ser numéricas 
 
           começando em zero, numérico começando em um ou alfabético. Especifique FMT usando uma série de zeros, uns ou a's, respectivamente. 
           O número de caracteres usados indica o comprimento desejado das extensões. Por exemplo, um especificador FMT de 0000 indica quatro 
           extensões numéricas de caracteres começando com 0000. 
 
    5. BYTES podem ser seguidos pelos seguintes sufixos multiplicativos: 
           c (1), w (2), b (512), kB (1000), K (1024), MB (1000*1000), M (1024*1024), GB (1000*1000*1000), G ( 1024*1024*1024), e assim por diante para 
           T, P, E, Z e Y 
            
           6. Considere usar cnt=, iskip= e oskip= para contornar 
 
           setores ilegíveis se a recuperação de erro falhar. 
 
    7. Enviar uma interrupção (por exemplo, CTRL+C) para dc3dd causará 
 
           o programa para relatar o trabalho concluído no momento em que a interrupção é recebida e, em seguida, sair. 
 
    dc3dd concluído em 2018-12-11 17:14:21 +0000 
 

    AUTOR Escrito por Paul Rubin, David MacKenzie, Stuart Kemp, Jesse Kornblum, Andrew Medico, Richard Cordovano e Justin Lowe. 

    RELATANDO BUGS Reporte bugs para dc3dd@dc3.mil . 

    DIREITO AUTORAL Copyright © 2008 Free Software Foundation, Inc. Licença GPLv3+: GNU GPL versão 3 ou posterior http://gnu.org/licenses/gpl.html Este é um software livre: você é livre para alterá-lo e redistribuí-lo . NÃO HÁ GARANTIA, na medida permitida por lei. 

    VEJA TAMBÉM A documentação completa para dc3dd é mantida como um manual Texinfo. Se os programas info e dc3dd estiverem instalados corretamente em seu site, o comando 

          info dc3dd 
 
    deve dar-lhe acesso ao manual completo. 
 

    dc3dd 7.2.646 dezembro de 2018 DC3DD(1) 

 
