* GRID
  -> É ultilizado para trabalhar os dois eixos X e Y no display.
  ex:
    display: grid;
    grid-template-columns: 200px 500px; ou 50% 50%; ou 1fr 2fr (esse significa fração/porção); 
  
  Outro ex:
    @media (min-width: 930px) { 
      main {
        grid-template-areas: 
          "A B B"
          "C C D";
      }

      main div:nth-child(1) {
        grid-area: A;
      }
      main div:nth-child(2) {
        grid-area: B;
      }
      main div:nth-child(3) {
        grid-area: C;
      }
      main div:nth-child(4) {
        grid-area: D;
      }
    }

* clamp()
  -> É uma função para ajuste de tamanho de letras, ele recebe tres agrumentos que é: 
      1º o valor minimo, 
      2º o valor ideal e 
      3º o valor máximo do tamanho dessa fonte.

    ex:   
      --fontSize-title: clamp(4rem, 1rem + 5vw, 5.6rem);

OBS: Testar os números conforme ficar agradável de olhar, em todas as opções de tela grande e/ou pequena.

    Outro exemplo:
    .page {
      max-width: clamp(33rem, 30rem + 20vw, 117rem);
      margin: 0 auto;
    }

* FILTER 
  ->É para aplicação de filtros, ex: 
    blur(5px), embaçar a imagem 
    brightness(), brilho
    contrast(), contrate
    drop-shadow(), sombras
    grayscale(), escala de cinza
    hue-rotate(), rotação da escala de hue
    opacity() saturate() -> pode ser feito junção de filtros também


* A variável no CSS, é para definição no inicio do projeto de algum dado que será muito ultilizado no decorrer do projeto. E se acaso ele precisar ser alterado em algum momento, não precisa mudar todas as linhas, apenas no inicio onde foi definida a variável.
  As variáveis do CSS normalmentesão aplicadas no :root{} que é o escopo/HTML geral da página.
  Elas são escritas começando por -- e o nome que vc quizer colocar, que seja alto didático.
  
  ex: 
    :root {
      --fontFamily-title: 'Epilogue', sans-serif; -> fonte de famila para todos os títulos principal
      --fontFamily-text: 'Open Sans', sans-serif; -> fonte de famila para todos os textos em geral
      --bkg-primary: #28293E;                     -> cor do background principal
      --fontColor-primary: #FFFFFF;               -> cor da fonte principal
      --fontColor-secondary: #BBB3E6;             -> cor da fonte secundária
    } 

Ai no decorrer do projeto, você vai chamando as variáveis conforme necessário.
  ex:
    body {
      background-color: var(--bkg-primary);
    }
    body h1 {
      font-family: var(--fontFamily-title);
      color: var(--fontColor-primary);
    }

    body p {
      font-family: var(--fontFamily-text);
      color: var(--fontColor-secondary);
    }

* Outra forma de usar as variáveis, é com a coloração. Aplicando a cor pela forma de hsla(), sendo que:
  h é a cor (hue), sendo ela ela pode ir do valor de 0, que começa no vermelho até o 360 que é o ultimo tom
  s é a saturação, que seria a força da cor, que fica na posição horizontal da tabela de cor
  l é a luminosidade, que seria mais claro e mais escuro, que fica na posição vertical da tabela de cor
  a é a opacidade, que vai de 0 a 1.

  OBS: Dessa forma você pode mudar todo o padrão da cor de todo o seu projeto.
    ex: 
      --hue: 250;
      --bkg-primary: hsl(var(--hue), 22%, 20%);
      --fontColor-primary: hsl(var(--hue), 0%, 100%);
      --fontColor-secondary: hsl(var(--hue), 50%, 80%); 


* TRANFORMAÇÃO AO PASSAR O MOUSE

img:hover {             -> aumenta a imagem de tamanho ao passar o mouse
  tranform: scale(1.1);
}

img {                 -> 1º chamar a propriedade e depois colocar as formas e tempos de transição
  transition-property: transform;
  transition-duration: 200ms;
  transition-timing-function: cubic-bezier(1,-0.19,0,1.11); -> esse item é manipulável
}

* TRANFORMAÇÃO AO INICIAR A PÁGINA
  -> para aplicar ultilizamos as @keyframes (pontos chaves), após colocamos o nome que quizermos, e dentro  da chaves colocamos o inicio e/ou meio e/ou fim, pode ter no minímo dois (inicio e fim) e/ou vários.
    Quando a animação chega/acaba no 100% ele volta ao estado original, ou pode ser ajustado com a propiedade forward de animation-fill-mode.

  * 1º você faz a instrução de criação da animação, por exemplo: 
      @keyframes topdown {    
        0% {        -> inicio
            opacity: 0;
            transform: translateY(-15px);
          }
          100% {
            opacity: 1;
            transform: translateY(0);
          }
        }

  * 2º faz a aplicação em qual elemento quizer:
      header {
        animation-name: topdown;
        animation-duration: 700ms;
        animation-fill-mode: forwards;   -> p/ ajustar o ponto fim, irá terminar com as propiedades do 100%
        animation-duration: reverse;     -> para executar a animação de 100% para o 0%
        animation-delay: 200ms;          -> para atrasar o inicio da 1º execução
        animation-iteration-count: infinite; -> para fazer a ação de forma infinita
        animation-play-state: paused;    -> para que a ação inicie pausada, e após passa o mouse 
                                            (:hover)  ele irá executar o comando      
        }
    * Configuração para iniciar o (:hover)
        header:hover {
          animation-play-state: running;
        }


