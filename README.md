# 1. Image Credits
All images on `lotr-flora/images` are licensed under either: the public domain/[CC0](https://creativecommons.org/publicdomain/zero/1.0/), [CC BY 2.0](https://creativecommons.org/licenses/by/2.0/deed.en), [CC BY 2.5](https://creativecommons.org/licenses/by/2.5), [CC BY 3.0](https://creativecommons.org/licenses/by/3.0), [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/), [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0), or free to use under the [Unsplash License](https://unsplash.com/license). Citations are given dynamically on page 7 of this [Data Studio report](https://datastudio.google.com/reporting/ec606261-78da-4474-8982-b4add0c5d762).

# 2. Files in This Repo
1. `flora_raw.csv`: contains raw data on LOTR plants.
2. `flora.csv`: contains the final, cleaned data on LOTR flora. For those interested in jumping straight to data analysis (as oppposed to replication of the construction of the dataset), work with this csv file.
3. `clean_flora_data.ipynb`: details the data cleaning process from the beginning file, `flora_raw.csv`, to the final file, `flora.csv`.
4. `chapters.csv`: contains the chapter name, the volume it's in, the book number, and the chapter's chronological ordering from 1-62.

# 3. Purpose
Anyone who’s ever read LOTR knows that Tolkien loves nature, especially plants. Plants are certainly mentioned a lot, but what is considered "a lot"? And just how rich is the flora of Middle-earth during the events of the War of the Ring? Answering those questions required data, which I didn’t have, and a love bordering on obsession for LOTR, which I do have. 

So, after months of reading, rereading, and proofreading, I present the LOTR flora dataset. I also made some vizzes of my findings, which you can find [here](https://datastudio.google.com/reporting/ec606261-78da-4474-8982-b4add0c5d762). 

This dataset contains the frequencies (and other related information) about plant names mentioned in J. R. R. Tolkien's main text of <i>The Lord of the Rings</i>. The motivation behind this project was to help readers who wish to know what the plants look like while reading the books. Just because a plant name has a frequency of 11 does not mean that specific word appeared in the text 11 times (e.g. "fir-needles" is counted under "fir", so "fir-needles" is not an entry in the dataset), nor does it necessarily mean that that specific plant was mentioned in the text 11 times (e.g. "butterbur" is a plant, but all 72 mentions of "butterbur" relate to the character Barliman Butterbur).

NOTE: This dataset contains aggregate statistical word frequency data derived from The Lord of the Rings by J. R. R. Tolkien. It does not contain full verbatim text or continuous passages from the original work.


# 4. Data Collection Methodology
For those interested in reconstructing my dataset for verification purposes, I have outlined my own procedure in the steps below. For those interested in understanding my data cleaning decisions, skip to downloading `clean_flora_data.ipynb`, as it contains comments detailing the cleaning process. For those interested in just downloading my dataset, feel free to disregard this whole `READ.me` and jump straight to downloading `flora.csv`. 

## 4.1. Materials
1. LOTR hardcovers, 2nd edition published by Houghton Mifflin
2. LOTR audiobooks narrated by Andy Serkis
3. [Search Tolkien](https://search.digitaltolkien.com/?terms=)
4. [Tolkien Glossary](https://glossary.digitaltolkien.com/)
5. Excel
6. A search engine and/or dictionary

## 4.2. Dataset Compilation
<ol>
  <li>Listen to the LOTR audiobooks (and/or read a physical LOTR copy)
    <ol>
      <li>Every time a new plant entity is mentioned, create a new row on an Excel spreadsheet and record the plant name on the row. Do not worry about frequency for now, just focus on getting every distinct plant name on the spreadsheet. As a strict rule, because I was interested in the specifics, I only included <i>explicitly named, specific plant entities</i>. 
        <ol>
          <li>Any linguistically related forms to the plant name (i.e. “fir-needles”, “fir-tree”, “fir-trees”, etc.) were all considered under the same plant name (i.e. “fir”).</li>
          <li>Any synonyms of a plant name were all considered under the same plant name (i.e “ling” is another word for heather, so “ling” and “heather” would not have two separate rows but rather consolidate under the same row “heather”). Make a note of any synonyms, as it will help with step 5 of data collection.</li>
          <li>Tolkien <a href="https://cite.digitaltolkien.com/LR/1.09.045/">stated</a> that many Shire and Bree residents have botanical names. Therefore, any names with clear botanical roots were also recorded (i.e. the last name “Mugwort” was recorded, even though it was only used in the text as a surname and not an actual plant. If you’re not sure whether something is a plant, that is what search engines are for.). Make a note of any plants that also inspired character names, as it will help with step 4.</li>
          <li>LOTR mentions wine several times, but never the plant used to make the wine, “grapes”. Therefore, neither “wine” nor “grapes” are included.</li>
          <li>Generic plant entities (i.e. “grasses”, “forest”, “heath”,  etc.) were excluded.</li>
          <li>Non plant entities (i.e. mushrooms, lichen, etc.) were excluded.</li>
          <li>Elvish names for plants were generally excluded unless:</li>
            <ol>
              <li>A common tongue equivalent was provided in the text (i.e. “athelas” also goes by “kingsfoil” and “asëa aranion”).</li>
              <li>It is clear from the context that the entity refers to a plant (i.e. Legolas sings a <a href="https://cite.digitaltolkien.com/LR/5.09.035/">song</a> about flowers and “mallos” is mentioned).</li>
        </ol>
          <li>Descriptors and references to the plant (i.e. “it”, “the sapling”, etc.) were excluded, with two exceptions:</li>
            <ol>
              <li>Pipeweeds: oftentimes, the text referred to the place that the pipeweed would grow in the same sentence as the word “pipeweed” but would not explicitly name the pipeweed (i.e. characters would <a href="https://cite.digitaltolkien.com/LR/6.06.096/">mention</a> “Southfarthing” while talking about both the place and the plant, but the actual mention of “Southfarthing” would be re: the place). I counted this as a mention of the pipeweed anyway because of how inherently connected the name of the pipeweed is to its place of cultivation.</li>
              <li>The lineage of the White Tree of Gondor (i.e. “Galathilion”, “Nimloth”, etc.): their details were meticulously provided in the LOTR index in the hardcover copies. Even if these references didn’t meet my “explicitly named, specific plant entities” rule, I included them anyway, because I also believe that <i>the primary text takes precedence over anyone’s interpretation of it</i> (the one person who is the exception to this rule is, in my opinion, Christopher Tolkien).</li>
            </ol>
    </ol>
  </li>
      <li>If reading with the audiobooks, cross-check throughout this process with the physical hardcovers of LOTR to make sure all plant names are caught.</li>
      <li>By the end of step 1, you should have finished reading LOTR and populated an Excel spreadsheet with only one column, named <code>plant</code>. The column has 116 different values (i.e. there are 116 different plant entities mentioned throughout the whole narrative). </li>
 </ol>
 </li>
    <li>Format the spreadsheet such that for every row (i.e. plant name), there are three columns: <code>fotr</code> (<cite>The Fellowship of the Ring</cite>), <code>tt</code> (<cite>The Two Towers</cite>), and <code>rotk</code> (<cite>The Return of the King</cite>).</li>
  <li>For every row on the Excel spreadsheet, search it up on Tolkien Glossary. This is the step that figures out the frequency of each plant entity.
    <ol>
      <li>For the <code>fotr</code>, <code>tt</code>, and <code>rotk</code> columns, record the chapter name (all lowercase but retaining all diacritics, spaces, and punctuation), followed by a semicolon, followed by the frequency of the plant name (i.e. <code>chapter name;frequency</code>). For multiple <code>chapter name;frequency</code> entries within the same column, separate them with a comma and no space afterwards  (i.e. <code>chapter 1 name;frequency,chapter 2 name;frequency,</code>...). Be careful not to make typos.
      <li>For plant names or forms that have multiple definitions (i.e. “rose” could refer to the flower but also the past tense of “rise”):</li>
      <ol>
        <li>Search up the term (i.e. “rose”) on Search Tolkien. </li>
        <li>Search Tolkien shows the exact lines in the text where the term is mentioned in the format <code>book.paragraph.sentence</code>, where all three semantic entities are expressed as numbers. Locate them all in the hardcover copies, and read their context. If the term was used in the text as a plant entity, include the occurrence as part of the count.</li>
      </ol>
      <li>By the end of step 3, you should have an Excel sheet with four columns populated: <code>plant</code>, <code>fotr</code>, <code>tt</code>, and <code>rotk</code>, with their respective values. Having empty cells is ok.</li>
      </ol>
  <li>Make another column, titled <code>name</code>, and another column, titled <code>real</code>.</li>
  <ol>
    <li>For every plant, indicate <code>“yes”</code> under <code>name</code> if the plant count also includes characters’ botanical names. Notes made from step 1.i.c. will facilitate this process quite quickly. Leave cells empty if not <code>“yes”</code>.</li>
    <li>For every plant, indicate <code>“no”</code> under <code>real</code> if the plant is fictional. They will be easy to determine, as they are all words that Tolkien invented or are part of the Middle-earth world building. Leave cells empty if not <code>“no”</code>.</li>
  </ol>
  <li>For the plants with synonyms, add to their <code>plant</code> name their synonyms in parentheses (e.g. <code>"heather (ling)"</code>)</li>
  <li>Export Excel to a csv file. Save as <code>flora_raw.csv</code> to the project directory. </li>
  <li>Download <code>chapters.csv</code>.</li>
  <ol>
    <li>Compiling this didn’t take too long, and it wasn’t compiled for data analysis more so than for utilitarian purposes to supplement the main flora dataset (<code>chapters.csv</code> introduces a natural ordering, which can help when visualizing plant mentions across chapters within a specific book or volume).</li>
    <li>The process for compiling <code>chapters.csv</code> isn’t included in detail for this reason. For those who wish to know, it was literally just <code>chapter</code>,<code>volume</code>,<code>book</code>,<code>order</code>, where <code>chapter</code> is the properly formatted chapter string, <code>volume</code> is the properly formatted volume string, <code>book</code> is the book number (<code>1</code>-<code>6</code>), and <code>order</code> is a number <code>1</code>-<code>62</code> (<code>1</code> means first chapter of LOTR, “A Long-expected Party”; <code>62</code> means the last chapter of LOTR, “The Grey Havens”).</li>
  </ol>
  <li>Download <code>clean_flora_data.ipynb.</code></li>
  <li>Run the Jupyter notebook with your exported csv. More detailed notes regarding data cleaning are in the notebook. By the end of step 9, you should have a fully cleaned LOTR flora dataset. </li>
</ol>

# 5. Notes
* Data only includes material from the main text of LOTR (i.e. excludes the prologue, appendices, *The Hobbit*, *The Silmarillion*, and all other works by J.R.R. Tolkien).
* As I’m not a botanist by profession, there were sometimes areas of confusion for me in determining whether a plant mention warranted a new row in my Excel spreadsheet. For example, “ilex” could refer to either “holm oak” or any plant of the genus *Ilex*, such as holly oak. In such cases of ambiguity, I erred on the side of caution and categorized them all as separate categories (the more general “oak” was also a separate category). This prevented their respective counts from conflating with each other.
* Some matches for “lily” actually meant “water-lily”, so the counts are reflected according to the correct reference.
* If a plant is mentioned as well as a more specific variety of the plant (i.e. brambles are of the genus *Rubus*, and blackberries are a type of berry that could be from a bramble), I included both.
* The plural form of “mallorn”, which is “mellyrn”, is also included in the count.
* I had to manually add the count for the iconic “po—ta—toes” line by Sam because it wasn’t showing up on Search Tolkien from a simple “potatoes” search.
* The LOTR index defers readers to “The Council of Elrond”, “The Siege of Gondor", and “The Steward and the King" for mentions of Nimloth. The index lists a mention of "the Tree" as Nimloth after King Elessar plants a new tree in Gondor, but I chose not to count this as a mention of Nimloth; the new tree is merely a descendant of Nimloth. Similarly, "the Tree" is listed under Nimloth in “The Steward of the King", but this was in reference to the withered Tree in Gondor, which I have counted under "white tree" instead. Those with a better understanding of the Silmarillion might categorize these counts differently.
* The LOTR index defers readers to “The Palantír” (referred to as the "White Tree" by Gandalf), “The Black Gate is Closed” (referred to as "the Tree of Silver"), and “The Steward and the King" for mentions of Telperion. In “The Steward and the King”, Telperion is mentioned by name once and referred to as the "Eldest of Trees" twice.
* The LOTR index defers readers to “The Palantír” (referred to as the "Golden" by Gandalf) and “The Black Gate is Closed” (referred to as "the Tree of Gold") for mentions of Laurelin. Galadriel's song in Farewell to Lórien mentions a "golden Tree"; although this mention is not listed in the index and its identity as Laurelin is up for debate, I have made the decision to consider this a mention of Laurelin.
* The “white tree” includes relevant matches for “white T/tree”, “withered T/tree”, “dead T/tree”, and “the Tree”, as well as any mentions that the index mentioned.
* “Briar” could refer to either the rose or blackberry bush, so for clarity, I put it as its own category.

# 6. Feedback and Contact
This dataset is also available on my [Kaggle](https://www.kaggle.com/datasets/lothlauren/lotr-flora). Feel free to leave a comment on the discussions there, or you can open an issue/pull request on Github, or contribute to the discussion. 
