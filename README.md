# R for Data Science (Edizione Italiana)

<!-- badges: start -->

[![Render and deploy Book to Netlify](https://github.com/hadley/r4ds/actions/workflows/build_book.yaml/badge.svg)](https://github.com/hadley/r4ds/actions/workflows/build_book.yaml)

<!-- badges: end -->

Questo repository contiene il codice sorgente della traduzione italiana del libro [R for Data Science](http://r4ds.hadley.nz).
Il libro è costruito usando [Quarto](https://quarto.org/).

## Traduzione Italiana

Questa è la traduzione italiana completa della seconda edizione di "R for Data Science" di Hadley Wickham, Mine Çetinkaya-Rundel e Garrett Grolemund.

## Immagini

### Disegni Omnigraffle

-   Font: 12pt Guardian Sans Condensed / Ubuntu mono

-   Esporta come png a 300 dpi.

-   Il font del sito web è 18 px = 13.5 pt, quindi scala dpi per far corrispondere le dimensioni del font: 270 = 300 \* 12 / 13.5.
    (Ho anche verificato questo empiricamente facendo screenshot.)

    ``` r
    #| echo: FALSE
    #| out.width: NULL
    knitr::include_graphics("diagrams/transform.png", dpi = 270)
    ```

### Screenshot

-   Assicurati di usare un tema chiaro.
    Per elementi di interfaccia piccoli (es. barre degli strumenti), ingrandisci due volte.

-   Screenshot con Cmd + Shift + 4.

-   Non è necessario impostare dpi:

    ``` r
    #| echo: FALSE
    #| out.width: NULL
    knitr::include_graphics("screenshots/rstudio-wg.png")
    ```

### O'Reilly

Per generare il libro per O'Reilly, costruisci il libro e poi:

```{r}
# pak::pak("hadley/htmlbook")
htmlbook::convert_book()

html <- list.files("oreilly", pattern = "[.]html$", full.names = TRUE)
file.copy(html, "../r-for-data-science-2e/", overwrite = TRUE)

pngs <- list.files("oreilly", pattern = "[.]png$", full.names = TRUE, recursive = TRUE)
dest <- gsub("oreilly", "../r-for-data-science-2e/", pngs)
fs::dir_create(unique(dirname(dest)))
file.copy(pngs, dest, overwrite = TRUE)
```

Poi commit e push su atlas.

## Codice di Condotta

Si prega di notare che r4ds usa un [Codice di Condotta per Contributori](https://contributor-covenant.org/version/2/0/CODE_OF_CONDUCT.html).
Contribuendo a questo libro, accetti di rispettare i suoi termini.
