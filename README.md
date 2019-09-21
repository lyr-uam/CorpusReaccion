# Corpus Reacción

## Responsable team:

Erika Sarai Rosas-Quezada, Gabriela Ramírez-de-la-Rosa, Esaú Villatoro-Tello

Research Group: Lenguaje y Razonamiento from Universidad Autónoma Metropolitana Unidad Cuajimalpa [lyr.cua.uam.mx](http://lyr.cua.uam.mx)

Licence: [**`CC-BY-SA-4.0`**](https://creativecommons.org/licenses/by-sa/4.0/) 

## Brief description

### Collect and share data from Public Pages in Facebook

This corpus is a collection of Spanish Facebook posts from public pages of known companies. The gathering and sharing of this corpus follows Facebook Policy at the time of recollection. Below, we cited some of the policies taken into account:

1. [Data Policy]([https://www.facebook.com/privacy/explanation](https://www.facebook.com/privacy/explanation)
   
   Under: *How is this information shared?* and then *People and accounts you share and communicate with* that states (bolds are ours)
   
   > **[Public information](https://www.facebook.com/help/203805466323736?ref=dp)** can be seen by anyone, on or off our Products, including if they don't have an account. This includes your Instagram username; any information you share with a public audience; information in your [public profile on Facebook](https://www.facebook.com/help/203805466323736?ref=dp); and content you share on a Facebook Page, [public Instagram account](https://l.facebook.com/l.php?u=https%3A%2F%2Fhelp.instagram.com%2F448523408565555%3Fref%3Ddp&h=AT3mch0p_K-9n-FqVgCT3-_IyVeeScZj2PcAgiTjWc9PyI69iS2qYWqDqhZnwfUhQFiSp5x9yqHY8MD4m7iLWFrezIj6Dt-CSyT3ugQXCoFzvBq61-n2IgH_5WLEeQ_U2d-6bZY31QkJ5lerHYNprbQX-ErTZQ) or any other public forum, such as [Facebook Marketplace](https://www.facebook.com/marketplace). You, other people using Facebook and Instagram, and we can provide access to or send public information to anyone on or off our Products, including in other Facebook Company Products, in search results, or through tools and APIs. **Public information can also be seen, accessed, reshared or downloaded through third-party services such as search engines, APIs**, and offline media such as TV, and by apps, websites and other services that integrate with our Products.

2. [Pages, Groups and Events Policies]([[https://www.facebook.com/privacy/explanation](https://www.facebook.com/privacy/explanation)]
   
   Under policy number 5: *Pages-Specific Policies* in *Content Visibility* that states 
   
   > Content posted to a Page is public and can be viewed by everyone who can see the Page

### Files in this data set:

This respository has 3 files:

* **CorpusReaccion_10Empresas.xml** contains a XML tree with information of 13651 Spanish written posts from 10 brands:
  
  * Clash Royale ES: [https://www.facebook.com/ClashRoyaleES/](https://www.facebook.com/ClashRoyaleES/)
  
  * Cinépolis: [https://www.facebook.com/cinepolisonline/](https://www.facebook.com/cinepolisonline/)
  
  * Canon Mexicana: [https://www.facebook.com/canonmexicana/](https://www.facebook.com/canonmexicana/)
  
  * Fisher-Price: [https://www.facebook.com/FisherPriceLatAm/](https://www.facebook.com/FisherPriceLatAm/)
  
  * Muy Interesante México: https://[www.facebook.com/MuyInteresanteMexico/
  
  * Discovery Channel España: https://[www.facebook.com/discoverychannelespana/
  
  * Xbox México: [https://www.facebook.com/xboxmexico/](https://www.facebook.com/xboxmexico/)
  
  * Lacoste: [https://www.facebook.com/LacosteMexico/](https://www.facebook.com/LacosteMexico/)
  
  * National Geographic: [https://www.facebook.com/natgeola/](https://www.facebook.com/natgeola/)
  
  * Nikon: [https://www.facebook.com/nikonmexico/](https://www.facebook.com/nikonmexico/)

* **true_labels.csv** contains a row for each post in the CorpusReaccion_10Empresas.xml file. For each row there are 7 columns as follows:
  
  * *post_id, impact_reactions, impact_comments, impact_shares, impact_positive_reaccions, impact_neutral_reactions, impact_negative_reactions*
  
  The values for each columns, except the post_id  is 1 or 0 to indicate a high or low impact, respectively.

* README.md 

#### Structure of the XML file:

Tag _Paginas_ (pages in English) is the root in the XML file. This root contains a node called _URL_ for each public page in our corpus (i.e. one tag for each public page of brand listed above).

Each _URL_ node contains two type of nodes: _Nombre_ (name) with the page name and *Publicacion* (publication). The *Publicacion* node can appear one or more times, one for each post in this particular public page.

Each _Publicacion_ node has:

* one node called *Fecha_Publicacion* (Publication date) with child nodes: _Hora_, _Dia_, _Mes_, _Anio_ (for Hour, Day, Month, and Year),

* three _Texto_ (Text) nodes. The first _Texto_ node contains the text exactly as has retrieve from the Facebook page. The second _Texto_ node contains the same text as in previous node but without the html elements. Finally, the third _Texto_ node contains the preprocessed text [^1]. 
  
  * For the preprocessed steps used in the third node we change mentions, hashtags and links for a particular word to represent each type of element.

* one or more nodes _Links_.

* one *Ejecucion_Programa* (programa_run) node that means to provide information for when the data was collected. Since this node contains one or more _Nodo_ (Node) tag. Each _Node_ has number of reactions, number of shares and numbers of comments on a post, and the exact date and time those numbers were collected.

An example of a XML file is shown below:

- ```xml
    <Paginas>
        <URL url="https://m.facebook.com/ClashRoyaleES/">
            <Nombre>Clash Royale ES</Nombre>
            <Publicacion id="437058360111686">
                <Fecha_Publicacion>
                    <Hora>13:51</Hora>
                    <Dia>7</Dia>
                    <Mes>08</Mes>
                    <Anio>2018</Anio>
                </Fecha_Publicacion>
                <Texto> El 13 de agosto para LATAM y 20 para Europa <span class="_5mfr"><span class="_6qdm" 
                        style="height: 16px;">😉</span></span>
                </Texto>
                <Texto>
                     El 13 de agosto para LATAM y 20 para Europa 😉
                </Texto>
                <Texto>
                     El 13 de agosto para LATAM y 20 para Europa <emoji>
                </Texto>
                <Link>https://supr.cl/&#8236;EsportsRoyaleES</Link>
                <Ejecucion_Programa>
                    <Nodo>
                        <Hora>3:51</Hora>
                        <Dia>25</Dia>
                        <Mes>11</Mes>
                        <Anio>2018</Anio>
                        <Me_Gusta>666</Me_Gusta>
                        <Me_Asombra>20</Me_Asombra>
                        <Me_Divierte>55</Me_Divierte>
                        <Me_Enoja>11</Me_Enoja>
                        <Me_Encanta>110</Me_Encanta>
                        <Me_Entristece>1</Me_Entristece>
                        <Veces_Compartido>16</Veces_Compartido>
                        <Comentarios>90</Comentarios>
                    </Nodo>
                </Ejecucion_Programa>
            </Publicacion>
        </URL>
    </Paginas>
  ```

## Acknowledgements

This project was funded by CONACyT Thematic Networks program (RedTTL Language Technologies Network) with project numbers: 281795 and 295022. 

[^1]: RosasQuezada: As we use it in **Predicting consumers engagement on Facebook based on what and how companies write**. Erika Sarai Rosas-Quezada, Gabriela Ramírez-De-La-Rosa and Esaú Villatoro-Tello. To be publish in Journal of Intelligent and Fuzzy Systems.
