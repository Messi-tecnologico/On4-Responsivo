# On4-Responsivo
Turma Online 4 | Front-end | 2019 | Semana 1 | Responsivo
---
## Layout Responsivo:

1 [Adaptativo e Responsivo](#layoutResponsivo)

2 [Resolução de tela x tamanho de tela](#resolucaoTamanho)

3 [Media Queries](#breakpointsMedia)

4 [Font-size e a Unidades de Medidas em Responsividade](#unidadesMedida)

5 [Imagens responsivas](#imagensResponsivas)

6 [O que é Mobile First](#mobileFirst)

7 [Display: flex](#displays)

8 [Cross-browser testing](#crossBrowser)

**[Exercício - Aula 25/10](#exercicio)**

* * * * *

<div id='layoutResponsivo'></div>

**ADAPTATIVO E RESPONSIVO:**

---

O conceito de *layout responsivo* surgiu em 2010, com o designer Ethan Marcotte
(https://alistapart.com/d/responsive-web-design/ex/ex-site-flexible.html https://alistapart.com/article/responsive-web-design) como uma forma de facilitar a adaptação de telas aos mais diversos tipos de tamanhos que começaram a surgir no mercado.

![gif-responsivo](https://cdn.dribbble.com/users/1112522/screenshots/5348827/mondrian-art-css-grid.gif)


* **Responsivo** e **Adaptativo** são praticamente a mesma coisa em se tratando de mudar a aparência/funcionalidade do site em diferentes tamanhos de telas - mais especificamente na largura (width)

  **Diferenças de termos:**

  * **Responsivo(grid fluido)**: ele 'responde' ao tamanho do browser, independente de marcação pontos específicos onde os tamanhos mudam, adaptando todo o conteúdo e funcionalidades.

  * **Adaptativo(media-queries)**: o conteúdo se molda em determinados pontos de mudanças de tamanho da tela. Estes pontos (breakpoints) são especificados no CSS, indicando qual conteúdo e como ele se modifica exatamente a partir desses pontos.

  ![adaptativo-responsivo](https://cdn-images-1.medium.com/max/1600/0*OVrwzPJUFzwId2gM.)

  **Pontos positivos Adaptativo:**
    * UX friendly: mantém o mesmo design adaptado para diferentes formatos de tela, sempre pensando na melhor usabilidade para cada formato;
    * É mais barato desenvolver um site responsivo do que ter que desenvolver versões diferentes do site, como uma versão mobile, por exemplo;
    * É mais fácil dar manutenção, porque o código está todo em um lugar só (se tivesse uma versão mobile e um app, por exemplo, uma mudança de código teria que ser feita em três lugares);
    * SEO friendly: como a aplicação só tem uma URL isso ajuda a manter todos os dados consistentes e a melhorar a posição no ranking do Google.

  **Pontos negativos Adaptativo:**
    * Normalmente os desenvolvedores testam o site nas principais resoluções/dispositivos disponíveis no mercado, porém é possível que em alguns dispositivos com formato de tela/resoluções não tão comuns o site não renderize conforme o esperado;
    * Versões antigas do IE;
    * Se o layout e a arquitetura do código não forem desenhadas antes de começar o trabalho, o site pode ficar muito difícil de manter/modificar;
    * O site responsivo pode ser mais demorado para carregar (se tiver muitas imagens redimensionadas, se tiver muitas chamadas externas de scripts, etc.).

* * * * *

  <div id='resolucaoTamanho'></div>

**RESOLUÇÃO DE TELA x TAMANHO DE TELA:**

---

  * Resolução de tela: A resolução da tela de um dispositivo é o número de pixels em cada dimensão que podem ser exibidos.

       ![pixel](https://www.exposureguide.com/media/resolution-of-the-image-in-pixels.jpg?x51595)

  * Tamanho de tela: tamanho físico da tela, normalmente medido em polegadas

       ![screens](https://res.cloudinary.com/practicaldev/image/fetch/s--Sed0tQ_i--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://cdn-images-1.medium.com/max/800/1%2AOkcOPoWR3bxKY2axlDX9UA.gif)

  A resolução de monitores de dispositivos digitais indica o número de pontos (ou pixels) que compõem a imagem que aparece na tela. Uma tela com 1920 x 1080 mostra 1920 pontos em cada uma das 1080 linhas do monitor!
  
  ![dpi](https://miro.medium.com/max/1240/1*nDCtsXEWZQotmCUQuR8jmQ.png)

  A qualidade da definição de uma imagem ou texto que aparece na tela depende da relação entre o número de pontos por polegada quadrada (ppi, pixels per inch) com que a tela está configurada, sua resolução nativa e o tamanho físico do monitor.

  Dispositivos com o mesmo tamanho podem ter resoluções de tela diferentes!

* * * * *

<div id='breakpointsMedia'></div>

**MEDIA QUERIES:**

---

 A partir de **breakpoints**, ou seja, tamanho de telas especificados pelo desenvolvedor, tem-se a variação do site de modo que todo o conteúdo/funcionalidades fique bem adaptados nessa telas.
 
No CSS, é onde são especificados esses breakpoints, e isso é pensado de acordo com as necessidades dos sites (público, negócio, etc)

   ![sizes](https://codetea.com/content/images/2017/04/Responsive-Pure-CSS-Masonry-Layout.gif)

Com as media queries e os breakpoints vamos começar a adicionar um pouco de lógica no css. O que vai acontecer é que o browser vai ler a folha de estilos, e SE a condição for verdadeira, ela vai executar o bloco de código, SENÃO ele vai apenas ignorá-lo.

  **SEMPRE LEMBRAR:**
  Sempre que trabalharmos com 'MEDIA QUERIES' temos que usar a metatag de nome VIEWPORT, da seguinte maneira:

  ```
   <head>
     <meta charset="utf-8">
     <meta name="viewport" content="width=device-width, initial-scale=1">
     <link href="css/style.css" rel="stylesheet">
   </head>
   ```

Esta tag diz ao browser para renderizar o conteúdo do site de acordo com os diferentes tamanhos dos dispositivos

A propriedade width controla o tamanho da viewport. O valor desta propriedade pode ser definido com um número específico de píxels como por exemplo width=600 ou com um valor especial chamado device-width que representa a largura da onde o conteúdo está sendo apresentado em pixels de CSS considerando uma escala de 100%. (Ainda há as propriedades height e device-height, as quais podem ser úteis para páginas com elementos que mudam de posição baseado na altura da viewport.)

A propriedade initial-scale controla o nível de amplificação quando a página é carregada pela primeira vez.

  * Trabalhando com 'MEDIA QUERIES':

    Se [largura do dispositivo] for menor ou igual a 768px, então execute o {...}
    ```
        @media (max-width: 768px) {
          .nome-da-classe {
            color: #fff; /* elemento que vai ser modificado/adicionado/sobrescrito nessa resolução */
          }
        }
    ```

    Se [largura do dispositivo] for maior ou igual a 768px, então execute o {...}
    ```
        @media (min-width: 768px) {
          .nome-da-classe {
            color: #fff; /* elemento que vai ser modificado/adicionado/sobrescrito nessa resolução */
          }
        }
     ```

    Se [largura do dispositivo] for entre 768px e 600px, então execute o {...}
    ```
        @media (max-width: 768px) and (min-width: 600px) {
          .nome-da-classe {
            color: #fff; /* elemento que vai ser modificado/adicionado/sobrescrito nessa resolução */
          }
        }
    ```


  /* esse é um bloco normal de css, o browser vai ler e mostrar esses valores na tela do usuário */
  ```
    .box {
      border: 1px solid #000;
      width: 320px;
      height: 120px;
      background-color: red;
    }
  ```

  /* esse é um bloco condicional, o browser vai ler e mostrar esses valores na tela do usuário SE a resolução da tela for menor que 768px */
  ```
    @media (max-width: 768px) {
      .box {
        background-color: blue;
      }
    }
  ```

  /* esse é um bloco condicional, o browser vai ler e mostrar esses valores na tela do usuário SE a resolução da tela for menor que 420px */
  ```
    @media (max-width: 420px) {
      .box {
        width: 100%;
        background-color: yellow;
      }
    }
  ```
  
  **GRID FLUIDO:**
  
É o uso de % ao invés de valores absolutos(px) para definir tamanhos de elementos no CSS. Essa é uma técnica que pode ser usada sempre, não apenas visando os layouts responsivos.

 **Para ler:** <https://www.w3schools.com/Css/css_rwd_grid.asp>

  **Importante:**
  Como o termo Responsividade é um conceito já implementado, ambos os casos - Adaptativo e Responsivo - são sempre               considerados RESPONSIVIDADE!

  Em nossa aula vamos focar no desenvolvimento da Responsividade com Media-Queries, ou seja, com 'breakpoints' definidos.
  Assim trabalharemos com os seguintes 'breakpoints':

  **1280px (desktop)**
  
  **768px (tablet - vertical)**
  
  **420px (mobile)**

* * * * *

<div id='unidadesMedida'></div>

**FONT-SIZE E AS UNIDADES DE MEDIDAS EM RESPONSIVIDADE:**

---

 Quando iniciamos o projeto de um site, é importante termos em mente que o browser já aplica um tamanho padrão de fonte.
 
 ![chrome](https://user-images.githubusercontent.com/42356402/67354393-62b5ef00-f52b-11e9-9f01-4d4b34325b98.png)
 
 Então se queremos alterar o tamanho da fonte para nosso projeto, teremos que aplicar medidas no CSS. Neste caso, podemos usar medidas absolutas (px), ou relativas(%, em, rem).

![measures](https://webandcrafts.com/blog/wp-content/uploads/2019/02/Relative-units.gif)

  **Medida absoluta:**
  
   * px: o pixel é uma medida fixa, logo absoluta. Quando aplicamos um valor para a fonte em px, dizemos ao navegador que o tamanho da nossa fonte será sempre aquele, independente de tamanho e resolução de telas.

  **Medidas relativas:**
  
   * em: Ao declararmos um valor com unidade em, dizemos que esse número é relativo ao tamanho da fonte do elemento pai.
    
   [![em](https://user-images.githubusercontent.com/42356402/67354175-c855ab80-f52a-11e9-982c-6f8cb1cf03a2.png)](https://codepen.io/gisantin/pen/qBBrZEy)
   
**Curiosidade: O em é uma maneira mais rápida de usar a porcentagem, e seu uso surgiu da época das gráficas de jornais impressos, que definiram o valor 1em como sendo o tamanho da letra "M", em maiúscula.**

    
   * rem("root em"): A unidade rem é relativa ao elemento root, ou seja, o valor da fonte definida no html ou body.
    Ex: 1em = valor declarado para a fonte onde ele esteja sendo usado
        1rem = valor declarado para a fonte na raiz do projeto (html, body)
        
   [![rem](https://user-images.githubusercontent.com/42356402/67407721-4eefa480-f58e-11e9-8854-e3210c4d4916.png)](https://codepen.io/gisantin/pen/WNNpwRG)
   
    
   * vh: viewport-height é nome para vh - quando se aplica a unidade vh, temos que o valor também aplicado é de 1% do valor da altura do container onde se está trabalhando(viewport).
    
   * vw: viewport-width é o nome para vw - quando se aplica a unidade vw, temos que o valor também aplicado é de 1% do valor da largura do container onde se está trabalhando(viewport).
   
   **Viewport** nada mais é que a área visível de uma página web para o seu usuário, essa viewport pode variar de acordo com o dispositivo, sendo menor em celulares e maior em desktops.
   
* * * * *

<div id='imagensResponsivas'></div>

**IMAGENS RESPONSIVAS:**

---

Ao se trabalhar com imagens em um projeto, devemos deixá-las escaláveis para responder proporcionalmente ao tamanho de variadas telas.
 
Um bom macete para fazer com que todas as imagens usadas no projeto sejam também responsivas, é criar uma classe no CSS, e aplicar essa classe em todas as tags de imagem do HTML.

```
.img-responsive {
  width: 100%;  ... terão sempre 100% de largura
  max-width: 100%;  ...aqui asseguramos que essa imagem não vai 'esticar'
  height: auto; ...a altura será sempre proporcional à largura
  display: block;
}
```


![image](https://www.elegantthemes.com/blog/wp-content/uploads/2018/09/5-column-layout-featured-image.jpg)




 **FORMATOS DE ARQUIVOS DE IMAGENS:**
 
   * JPEG ou JPG: mais popular e permite compressão de imagens. Salvar em JPG imagens mais simples que não precisem ser aumentadas
   * PNG: imagens com transparência e melhor qualidade. Também permite compressão e com qualidade melhor que JPG mas são arquivos mais pesados.
   * SVG: É um vetor e não uma imagem. Ele é um arquivo com instruções xml que criam um desenho vetorizado na tela. O .sg não perde qualidade e pode ser ampliado quase infinitamente. É recomendado para ícones e logotipos.
   * GIF: Permite salvar animações, porém com qualidade de imagem bem ruim. onde

* * * * *

<div id='mobileFirst'></div>

**O QUE É MOBILE FIRST:**

---

Quando construimos o nosso projeto para que seja prioritariamente visualizado em formato mobile. Assim a contrução do nosso CSS parte de configuraçao e funcionalidade que serão usados em devices menores, como um celular, por exemplo.

  **Por que é importante?**
  
O celulares ou tablets, aparelhos cada vez mais portáteis, são os principais meios de acesso à internet. Logo, desenvolvermos sites priorizando a performance nesses aparelhos é muito importante para um negócio\produto.

Mas é bem importante trabalhar bem o CSS de modo a não deixar perder funcionalidades em telas maiores.

Ex: Nosso ponto de partida é uma tela 768px. Ao invés de mudar os estilos à medida que a largura fica menor que 768px, nós devemos mudar o estilo da página à medida que a largura fica maior que 768px. Isso faz o nosso projeto Mobile First!

  ![mobile-desktop](https://urucumdigital.com/wp-content/uploads/2019/08/3038367-slide-s-8-9-gifs-that-explain-responsive-design-brilliantly-08desktop-first-vs-mobile-first-3.gif)


* * * * *

<div id='displays'></div>

**DISPLAY: FLEX :**

---

 A propriedade de css display: flex permite alinhar com facilidade elementos lado a lado.
 
 Você deve adicionar a propriedade no elemento pai para alinhar o conteúdo filho lado a lado.
 
![flex-direction](https://cdn-media-1.freecodecamp.org/images/HHwxqz2N4bNksz9YwcMBAtD0z9TTCxeNXNBS)
 
```
<nav class="container">
  <div>Home</div>
  <div>Busca</div>
  <div>Sair</div>
</nav>

.container {
  display: flex;
}
 ```
 
  ![flexbox](https://cdn-media-1.freecodecamp.org/images/6WwoIEc45lUHUcFQCmD8GmziiISm2lO64Y1-)

O display: flex tem propriedade complementares que permitem alinhar os elementos filhos ao centro, à direita, à esquerda, tanto na horizontal como na vertical.

**Exercício para treinar:** <https://flexboxfroggy.com/#pt-br>

Guia Flexbox: <https://css-tricks.com/snippets/css/a-guide-to-flexbox/>

* * * * *

<div id='crossBrowser'></div>

**CROSS-BROWSER TESTING:**

---

Testar seu projeto ou aplicação em diferentes navegadores (browsers) e observar se todos ou a maioria deles mantém estilo e funcionalidades originais sem comprometer sua qualidade de navegaçao/usabilidade.
 
 ![browsers](https://i.pinimg.com/originals/8c/0b/27/8c0b2725800f5939902ece759c9129ef.gif)

  **Como testar?:**
  * BrowserStack
  * Google insights
  * What is my screen resolution
  * Chrome DevTools

* * * * *

<div id='exercicio'></div>

## Exercício - Aula 25/10

---

**Página de Currículo pessoal:**

Vamos usar o projeto que desenvolvemos no Workshop - Currrículo Pessoal - e vamos trabalhar a aplicação do conceito de responsividade.

   ![pag-1](https://user-images.githubusercontent.com/42356402/67355374-7febbd00-f52d-11e9-866c-d96b13902bc6.png)
   
   ![pag-2](https://user-images.githubusercontent.com/42356402/67355439-a4e03000-f52d-11e9-84b9-da8399a2a27a.png)
   
   
Utilizaremos os seguintes breakpoints:
 
 **1024px(tablet horizontal)**
 
  **768px (tablet - vertical)**
  
  **420px (mobile)**
  
  **375px (mobile)** 
 
 O ideal para o exercíco é escrever pelo menos dois breakpoints, de modo que se vejam mudanças entre um e outro. 
 Para treinar, podem desenvolver em todos os sugeridos ou mais! =)
 
 **DICA:** Pesquisem modelos de layout responsivo na internet (Pinterest, Google etc...) e veja como/quais elementos se adequam melhor a cada breakpoint!!!


* * * * *

Links para consulta:

<https://css-tricks.com/the-difference-between-responsive-and-adaptive-design/>

<https://nextecommerce.com.br/design-responsivo-ou-entrega-adaptativa-o-que-e-melhor-para-o-marketing-digital/>

<https://www.freecodecamp.org/news/how-to-make-your-html-responsive-by-adding-a-single-line-of-css-2a62de81e431/>

<https://drafts.csswg.org/css-values-3/#font-relative-lengths>

<https://tableless.com.br/manipulando-metatag-viewport/>

<https://www.w3schools.com/Css/css_rwd_mediaqueries.asp>

<https://blog.caelum.com.br/flexibilidade-em-paginas-para-dispositivos-moveis-com-media-queries/>

<https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Box_Alignment_in_CSS_Grid_Layout>

<https://www.freecodecamp.org/news/an-animated-guide-to-flexbox-d280cf6afc35/>

<https://www.softwaretestinghelp.com/how-is-cross-browser-testing-performed/>



