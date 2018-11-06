# Melhores práticas de acessibilidade

Este é um espaço para construirmos um guia de melhores práticas de acessibilidade para quem trabalha com a produção do formato ePub3.

**Versão:** 0.1 
**Data:** agosto 2018

# Dicas práticas 

## Todo texto deve ser disponibilizado em uma ordem de leitura lógica
Já fazemos isto, de alguma forma, quando produzimos um ePub, porém precisamos estar mais atentos quando temos boxes ou quadros de textos que quebrem a narração.

No livro impresso é bem comum termos estes elementos que aparecem ao lado do texto. No ePub precisamos colocar eles em uma ordem de leitura coerente e bem estruturada no HTML. Não use reposicionamento com CSS ou mesmo texto em forma de imagem.

Use corretamente os tags de estrutura que o HTML5 oferece (\<section\>, \<article\>, \<header\>, etc...) para criar uma ordem de leitura principal e outros tags específicos para os elementos auxiliares, como notas de rodapé, quadros de textos, referências.

## Separe sempre o conteúdo da apresentação
Isto é possível fazer usando corretamente o CSS e o HTML. Lembre-se HTML serve para criar a estrutura do texto e é o CSS quem cuida da apresentação visual. O significado do texto deve permanecer o mesmo seja com o design aplicado ou sem ele.

Outra anotação importante é a de não usar tabela para forçar uma formatação visita do texto; nem use somente as cores como indicação da importância de uma palavra.

É importante lembrar que os tags <strong\> e <em\> não significam apenas bold e itálico, mas carregam com eles mais significados que podem ser interpretados pelos softwares leitores de tela.

## Uso de sumários e sistemas de navegação
Inclua sempre um sumário bem completo. Aliás, é possível incluir até mais de um sumário. Você pode assim especificar melhor os conteúdos presentes no livro. Estruturando bem o tag <section\> e o tag <aside\> você vai poder fornecer uma ordem de leitura lógica e bem organizada.

## Crie uma estrutura significativa
Use sempre os tags corretos de títulos (\<h1\>, \<h2\> etc..) na ordem correta e sem pular de níveis. Não use os tags para definir design! Para isto existem as classes! O livro deve apresentar um uso coerente destas etiquetas de títulos.

É fundamental conhecer o uso do epub:type. Este atributo explica o que o elemento é. Por exemplo um \<section epub:type=“preface”\> indica que este é um bloco de texto que chamamos de Prefácio. Aqui entra também o uso do WAI-ARIA, que vai a se sobrepor ao ePub:type e fornece também um significado para a tag. Assim nosso texto ficaria \<section epub:type=“preface” role=“role-prefacie”\>.

Uma curiosidade: você sabia que o \<small\>, muitas vezes usado para criar um texto em “falso versalete” deveria ser usado apenas para os textos “pequenos”, não em tamanho, mas em significado, ou seja, aqueles textos que completam algo, como por exemplo a informação de copyright:

\<p\>Booknando - Consultoria, formação e produção de livros digitais\</p\>
\<p\>\<small\>Copyright 2018 by Booknando Livros LTDA\</small\>\</p\>


## Defina o conteúdo de cada etiqueta
Isto tem tudo a ver com o ponto 4. O uso correto do WAI-ARIA e do epub:type permite definirmos a função de cada elemento. Isto é muito importante para que o software de leitura de tela, o screen reader consiga fornecer esta informação a quem está escutando o texto.

Por exemplo a entrada \<dl epub:type=“glossary”\> indica que o tag \<dl\> esta sendo utilizado para formatar um glossário.

Use o EPUB 3 Structural Semantics Vocabulary para identificar o conteúdo.

## Use imagens somente para imagens e não para tabelas ou texto
Bem, esta é uma pratica que deveria ser evitada sempre. Inclusive a Amazon indica isto como um erro de produção. Quando colocamos um texto em forma de imagem automaticamente perdemos a possibilidade de utilizarmos em uma busca ou indexação de conteúdo e os softwares leitores não conseguem “ler” o que está escrito.

Caso seja impossível não usar uma imagem, acrescente uma descrição clara e objetiva. Para gráficos é possível optar por SVG que permite descrições de acessibilidade de conteúdo.

## Use o tag alt para a descrição das imagens
Todas as imagens devem ser fornecidas com um texto alternativo. Este trabalho de descrição pode ser feito por uma empresa ou pessoa especializada, mas seria interessante que o autor esteja também envolvido neste processo de produção, afinal é ele quem sabe a função principal daquela imagem.

Na página do Diagram Center vocês encontram algumas indicações de como fazer uma boa descrição de imagem.

O texto alternativo além de oferecer acessibilidade pode ajudar nos motores de pesquisas, como o Google: “O google é o deficiente visual mais famoso que existe. Ele enxerga somente texto.” (@msales no vídeo https://youtu.be/wjZEPeTwVL4)

O google é o deficiente visual mais famoso que existe. Ele enxerga somente texto. @msales
Algumas dicas práticas sobre descrição em imagens você pode encontrar nestes slides: https://pt.slideshare.net/julianafrost.

## Inclua uma numeração de página
Este requisito é muito importante para livros didáticos ou acadêmicos que podem ser utilizados em sala de aula juntos com livros impressos. Isto facilita muito o acesso ao conteúdo por parte dos alunos/leitores.

Este recurso fornece também outra forma de navegar pelo livro, além de ser de fundamental importância caso você queira criar um índice remissivo.

Com o atributo epub:type=“pagebreak” você define as páginas no texto. Recomendo colocar a indicação no início do texto da página, para ser mais fácil encontrar o conteúdo. Você não precisa deixar o número aparecendo no meio do texto, pode definir apenas como âncora no texto:

\<span id="pag45" epub:type="pagebreak" /\>
Depois disto vai ser necessário acrescentar lá no documento de navegação, o toc.xhtml, as referências para estas âncoras.

## Defina a língua do documento
Algo que em geral não se faz nos eBook mas que é fundamental quando falamos de acessibilidade é definir dentro do tag HTML principal a língua do documento. Ainda que esta já tenha sido definida nos metadados você deve acrescentar também em cada documento a informação xml:lang= “pt” lang= “pt”.

Caso exista um parágrafo ou uma citação em lingua diferente basta acrescentá-la no texto: \<span xml:lang=“fr” lang=“fr”\>rue Saint-Andre-des-Arts\</span\>.

## Use o MathML
Para as equações matemática é recomendado o utilizo do MathML para que seja eliminada a ambigüidade na leitura de uma imagem. Também é possível o uso do SVG com uma adequada descrição.

O uso do MathML é controverso porque nem todos os softwares leitores o suportam de maneira correta, mas este é um problema que tende a diminuir sempre mais, na medida que os softwares estão sendo atualizados. Para se ter uma ideia inicial do suporte fornecido a este recurso consulte esta tabela http://docs.mathjax.org/en/latest/misc/epub.html.

Recomendo dar sempre uma olhada na tabela do BISG, (http://epubtest.org/) que fornece muitas indicações sobre o suporte que os softwares leitores oferecem ao ePub3.

## Forneça um acesso alternativo ao conteúdo multimídia
Caso você faça uso de vídeo ou áudio no seu livro forneça sempre outro modo de acesso a estes elementos. Por exemplo, você pode fornecer legendas para os vídeos ou uma transcrição para o áudio.

## Inclua interações acessíveis
Quando fizer uso de SVG ou de javascript (são poucos os casos), certifique-se que estas interações sejam acessíveis. Os controles das interações devem utilizar a fundo o ARIA, indicando os atributos apropriados (roles, states, e properties).

## Use os metadados de acessibilidade
Além dos metadados normais do seu eBook é importante acrescentar informações específicas de acessibilidade. Estes metadados deverão estar no content.opf e fornecem aos softwares de leitura informações sobre o tipo de conteúdo que o livro contém. Além disto os sistemas de buscas podem identificar mais facilmente o arquivo como acessível.

## Enfim, certifique-se que as indicações acima sejam realmente aplicadas.
Não deixe de iniciar um processo dentro de sua empresa para que a acessibilidade seja implementada em toda a cadeia produtiva.

Desenvolva um guia de boas práticas e um bom checklist que ajude o designer e o desenvolvedor de livros digitais a aplicar todos estes recursos.

Faça com que todos os envolvidos no fluxo de produção entendam bem o que é acessibilidade e saibam como implementá-la. Do autor à quem faz o cotejo do livro é importante que todos estejam conscientes que acessibilidade não é um recurso mas sim um requisito básico das publicações digitais.


## Fonte:
Estas dicas foram publicadas originalmente pelo Diagram Center que é uma iniciativa da BENETECH empresa sem fins lucrativos especializada em livros acessíveis. O meu texto não é uma tradução fiel mas uma adaptação. ↩︎


# Tradução a ser feita

Texto traduzido de
http://www.accessiblebooksconsortium.org/publishing/en/accessible_best_practice_guidelines_for_publishers.html
para o português por José Fernando Tavares - Booknando Livros

Tradução em andamento.
