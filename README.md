# search_specielink
Função para realizar buscas na versão mais recente do portal SpeciesLink.net. Para isso é necessária uma chave API (obtida em: https://specieslink.net/aut/login/?next=/aut/profile/apikeys)

## Uso:
 
 Você pode utilizar os seguintes argumentos na função:

   - apikey: Chave de autenticação para acessar a API do speciesLink, necessária para fazer requisições.
   - dir: Diretório onde os arquivos serão salvos, o padrão é "results/".
   - filename: Nome do arquivo de saída sem extensão, o padrão é "output".
   - save: Boleano que indica se os dados retornados devem ser salvos localmente, o padrão é FALSE.
   - basisOfRecord: Tipo de registro (PreservedSpecimen ou LivingSpecimen), define a base dos dados a serem buscados.
   - family: Nome da família taxonômica, apenas registros dessa família serão retornados.
   - species: Nome científico da espécie, apenas registros dessa espécie serão retornados.
   - collectionCode: Código de coleção, define o conjunto específico de dados dentro do banco de dados.
   - country: Nome do país, limita os dados ao país especificado.
   - stateProvince: Nome do estado ou província, filtra os registros por essa região.
   - county: Nome do município, limita os dados ao município especificado.
   - bbox: Limite espacial (bounding box), define uma área geográfica em coordenadas [xmin, ymin, xmax, ymax].
   - Coordinates: Qualidade das coordenadas (Yes, No, Original, Automatic, Blocked).
   - CoordinatesQuality: Qualidade das coordenadas (Good ou Bad).
   - Scope: Escopo dos dados (plants, animals, microrganisms, fossils).
   - Synonyms: Filtro de sinônimos com base em bases de dados específicas (species2000, flora2020, etc.).
   - Typus: Boleano para incluir registros de tipos nomenclaturais, o padrão é FALSE.
   - Images: Tipo de imagens a serem incluídas (Yes, Live, Polen, Wood).
   - RedList: Boleano ou filtro para registros relacionados à Lista Vermelha (ex.: all para todos os status).
   - MaxRecords: Número máximo de registros a serem retornados, deve ser maior que 0.
   - file.format: Formato do arquivo de saída (csv ou rds).
   - compress: Boleano que indica se o arquivo de saída deve ser compactado, o padrão é FALSE.

Mais infomações sobre os argumentos usados na função podem ser consultados em: https://specieslink.net/ws/1.0/.

A função rspeciesLink2.0 retorna um data frame com registros recuperados da API speciesLink. O conteúdo inclui informações taxonômicas, localização, tipo de registro e outros metadados, dependendo dos filtros aplicados. Se solicitado (save = TRUE), os dados também podem ser salvos em arquivos csv ou rds. Caso a consulta não retorne resultados, um aviso será emitido.


``` r
#Uso básico para encontrar espécies vegetais ocorrentes em uma dada área (aii_bb).
aii_bb <-c("-35.060998", "-7.461548", "-34.801723", "-7.296315")
rspeciesLink2.0(apikey= "SUA API", bbox = aii_bb,
                   save=F, file.format="csv",  
                   Scope = "plants", Synonyms = "flora2020")
                   
```
