# Lägga Till Uppgifter i Taskmator Med Drafts

_Captured: 2016-01-10 at 10:28 from [www.appleyra.se](http://www.appleyra.se/genomgangar/lagga-till-uppgifter-i-taskmator-med-drafts/#nogo)_

I min artikel om [hur jag anvander Taskmator och Fantastical](http://www.appleyra.se/genomgangar/hur-jag-anvander-taskmator-med-fantastical-och-drafts/) namnde jag att jag anvander Drafts for att lagga till uppgifter. Det ar nu dags att forklara varfor och hur detta gar till.

![Drafts 4](http://i1.wp.com/media.agiletortoise.com/drafts4-press-kit/drafts4-banner/drafts4-banner-880x220.png?resize=660%2C165)

> _Drafts 4_

## Inledning

Det ar flera anledningar till att jag valt att anvanda Drafts och inte det inbyggda URL-schemat i Taskmator. Den storsta anledningen ar jag vill ha nya uppgifter overst i dokumentet men URL-schemat stodjer bara att lagga till i slutet. Dessutom ar Drafts snabbare och kan lagga till i bakgrunden utan att oppna Taskmator.

## Utforande

For att fa det hela och funka har jag skapat en atgard i Drafts som bestar av 3 steg. Det forsta steget ar ett script som lagger till `-` fore varje rad som inte ar indragen. Nasta steg ar att visa en meny med filnamnen pa filerna jag anvander. Efter jag valt fil sa anvander jag en inbyggd funktion for att lagga till overst (prepend) i ett dokument i Dropbox.

### Script for att lagga till bindestreck

Drafts kan anvanda sig av JavaScript for att paverka texten och innehallet. Eftersom jag inte ar nagon expert pa JavaScript har jag utgatt fran ett [script av Macdrifter](http://www.macdrifter.com/2015/01/the-drafts-inbox-for-plain-text-tasks.html). Sen har jag andrat i det for att fa det som jag vill. Gabe's script ar mycket smartare an mitt men passade inte med hur jag jobbar. Scriptet lagger till ett bindestreck och ett mellanslag i borjan pa raden, borjar raden med en `tab` sa hoppar den over den. Jag anvander indragningen for att lagga till en anteckning till uppgiften och vill inte att de ska bli omvandlade till uppgifter. Eftersom jag har testat mig fram sa gar det sakert att effektivisera och gora sjalva scriptet _snyggare_. Men jag nojde mig med att det far jobbet gjort.
    
    
    // Script keys run short Javascripts
    // For documentation and examples, visit:
    // http://help.agiletortoise.com
    
    //   Function to remove multiple line breaks
    function removeBlanks(txt){
        txt = txt.replace(/(\r\n|\r|\n)+/g, '$1')
        return txt;
    }
    // Function to Prefix each line of a text block
    function textPrefix(textStr, preFix){
    var i= 0;                
    var array1 = textStr.split("\n");
    // Regex for one or more tabs
    // re = /^\t{1,}/;
    // Split the text into lines stored in an array
    for ( i = 0; i < array1.length; i++) {
        // Skip lines that are just blank
        if (array1[i] !== ""){
            taskString = array1[i];
            var tabPrefix = "";
      // Check to see if it's a project
            var projMatches = removeBlanks(array1[i]).match(/^\t{1,}/);
    
            if (projMatches == null){
                // If it's not a project then add the hyphen and tabs
                array1[i] = tabPrefix + preFix + taskString;
            } else{
                // Otherwise just put the tabs back
                array1[i] = tabPrefix + taskString;
            }
        }
    }
    // Put all the lines back together
    val = array1.join("\n");
    return val;
    }
    // This is how we change the content in Drafts
    var sel = draft.content;
    // Call the function with a prefix for TaskPaper tasks
    draft.content = (textPrefix(removeBlanks(sel), "- "));
    commit(draft);
    

### Skapa en meny med val

Nasta steg ar en inbyggd funktion som kallas _Prompt_ och ger dig mojligheten att fa upp en ruta att skriva i. Du kan ocksa specificera vilka knappar som ska finnas och det ar den funktionen jag anvander mig av. Vill du ha flera knappar sa separerar du de med `|`. For att underlatta har jag samma namn pa knapparna som dokumenten i Dropbox och far foljande lista. `tpHem|tpLinEdu|tpApps|tpAppleyra|tpBooks|tpFilmer`. Det dokument jag valjer har sparas i en variabel och anvands i sista steget.

![Lista i Drafts](http://i1.wp.com/www.appleyra.se/wp-content/uploads/2016/01/Drafts-taskmator.jpg?w=660)

> _Lista i Drafts_

### Lagga till uppgifter i dokumentet i Dropbox

Sista steget bestar i att ta texten och lagga till den overst i det dokument som jag valde i menyn. For det anvander jag ytterligare en inbyggd funktion som kort och gott heter _Dropbox_. Har valjer jag filnamn, filtillagg, sokvag, innehall och om jag vill skapa ny, ersatta, lagga overst (prepend) eller underst (append) i dokumentet. Som filnamn valjer du variabeln fran menyn genom att skriva `[[prompt_button]]`, som filtillagg har jag taskpaper och jag har valt pretend som metod. Till innehall anvander jag variabeln `[[draft]]` som tar all text jag skrivit och lagger till i dokumentet.

## Snabbare atkomst med en genvag

For att ytterligare snabba pa processen anvander jag en genvag i det den utokade raden ovanfor tangentbordet. For att lagga till en atgard dar scrollar du langst bort i raden och knackar pa pennan. Har knackar du pa \+ och valjer `Run Action`i listan som dyker upp. Nasta steg ar att valja text for knappen och fylla i namnet pa atgarden som ska koras. Jag har aven lagt till ett kortkommando pa tangentbordet sa jag kan kora den fran ett externt tangentbord.

![Skapa en genväg till åtgärd](http://i1.wp.com/www.appleyra.se/wp-content/uploads/2016/01/drafts-action-key.jpg?w=660)

> _Skapa en genvag till atgard_

## Sammanfattning

Drafts ar verkligen ett multiverktyg som jag har stor anvandning for. Denna atgard gor att det gar otroligt snabbt att lagga till uppgifter i [Taskmator](https://itunes.apple.com/se/app/taskmator-taskpaper-client/id806250172?mt=8&uo=4&at=10lKZy&ct=twitter). Jag [gar igenom listorna varje morgon](http://www.appleyra.se/genomgangar/hur-jag-anvander-taskmator-med-fantastical-och-drafts/) och flyttar uppgifter till ratt projekt. Mojligheten att snabbt kunna _tomma hjarnan_ gor att jag glommer farre saker och kan koncentrerar mig battre pa det jag haller pa med for tillfallet.

**[Drafts 4 - Quickly Capture Notes, Share Anywhere!](https://itunes.apple.com/se/app/drafts-4-quickly-capture-notes/id905337691?mt=8&uo=4&at=10lKZy&ct=appleyra) ar en universal-app som finns att hamta pa App Store [109 kr]**

  

