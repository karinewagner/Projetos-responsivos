Regra nº 1:
  Sempre desenvolver primeiro para modile, pois como o fluxo do html já um bloco abaixo do outro, assim ficará bem mais facil, depois só quebrar / ajustar os blocos para aparência para desktop.

  OBS: Já tentar montar o HTML estruturado para os dois (Mobile e Desktop), com as devidas tags.

Regra nº 2:
  Sempre desenvolver com unidade de medida em REM e não por PX para melhor acessibilidade.
  Para padronização, sempre colocar no inicio dos projetos
  :root {
    font-size: 62.5%; /* Que equivale a 10px */
  }
  
    E após essa configutação sempre informar as medidas como rem.
      EX: 16px = 1.6rem, 60px = 6.0rem, 40px = 4.0rem...

      OBS: Quando o numero for menor que 4px, não precisa ajustar para rem, pois não fará muito diferença e mantem o layout coerente
          EX: para uso em bordas, ou espaço entre letras

Regra nº 3:
  padrões da propriedade meta do HTML pré definido para a -> viewport
  no CSS usamos a @media, que são as medias queries
    
    ex: @media (min-width: 40em) { 40em = 640px
          body {
            background-color: black;
          }
        }




Padrão do display flex:
    display: flex;
    align-items: flex-start;
