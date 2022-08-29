### Build_and_Deploy_a_Modern_Full_Stack_Social_Media_App

#**Passo a passo do projeto Social Media App**

[Link do Vídeo do projeto](https://lnkd.in/dKVy8APi) 

- [X] **1) Criar pasta e baixar Sanity** 

:heavy_check_mark: pasta e projeto no GitHub: *Build_and_Deploy_a_Modern_Full_Stack_Social_Media_App*

:heavy_check_mark: subpastas:
	
	socialMedia_backend
	
	socialMedia_frontend

:heavy_check_mark: Comandos no terminal:

:heavy_check_mark: mudar diretório: cd .\socialMedia_backend\

:red_circle: Depois de fazer login no site da sanity

[Link site Sanity](https://www.sanity.io/javascriptmastery )

:heavy_check_mark: instalar sanity:		*npm install -g @sanity/clinpm install -g @sanity/cli* 

Obs.: não funcionou esse comando acima no terminal então usei o comando sugerido no vídeo *npx sanity init*

:heavy_check_mark: executar sanity: *sanity init --project-plan boosted-free-2021-12-08* 

:heavy_check_mark: Select project to use *Create new project*

:heavy_check_mark: Your project name: *socialMedia_jsm*


> ? Use the default dataset configuration? *Yes*

> Creating dataset

> ? Project output path: C:\Users\phenr\OneDrive\Área de Trabalho\Stefany\Projetos_Programacao\Build_and_Deploy_a_Modern_Full_Stack_Social_Media_App\socia
lMedia_backend

> ? Select project template *Clean project with no predefined schemas*


:heavy_check_mark: *sanity start*

:heavy_check_mark: *sanity manage*

- [X] **2) Programação Backend** 

:question: **TESTE 1**

:heavy_check_mark: socialMedia_backend -> schemas -> user.js

```
export default{
    name:'user',
    title:'User',
    type:'document',
    fields:[
        {
           name: 'userName',
           title: 'UserName',
           type: 'string'
        },
        {
            name: 'image',
            title: 'Image',
            type: 'string'
         },
    ],
};
```
:heavy_check_mark: socialMedia_backend -> schemas -> schema.js

```
// First, we must import the schema creator
import createSchema from 'part:@sanity/base/schema-creator'

// Then import schema types from any plugins that might expose them
import schemaTypes from 'all:part:@sanity/base/schema-type'
import user from './user'


// Then we give our schema to the builder and provide the result to Sanity
export default createSchema({
  // We name our schema
  name: 'default',
  // Then proceed to concatenate our document type
  // to the ones provided by any plugins that are installed
  types: schemaTypes.concat([ 
    user
  ]),
});

```

:sparkles: Funcionou!!!

:question: **TESTE 2**

:heavy_check_mark: socialMedia_backend -> schemas -> pin.js

```
export default{
    name:'pin',
    title: 'Pin',
    type: 'document',
    fields: [
        {
            name: 'title',
            title: 'Title',
            type: 'string', 
        },
        {
            name: 'about',
            title: 'About',
            type: 'string', 
        },
        {
            name: 'destination',
            title: 'Destination',
            type: 'url', 
        },
        {
            name: 'category',
            title: 'Category',
            type: 'string', 
        },
        {
            name: 'image',
            title: 'Image',
            type: 'image',
            options: {
                hotspot: true
            } 
        },
        {
            name: 'userId',
            title: 'userId',
            type: 'string', 
        },
        {
            name: 'postedBy',
            title: 'PostedBy',
            type: 'postedBy', 
        },
        {
            name: 'save',
            title: 'Save',
            type: 'array', 
            of : [{ type: 'save'}]
        },
        {
            name: 'comments',
            title: 'Comments',
            type: 'array', 
            of : [{ type: 'comment'}]
        },
    ]
}
```
:heavy_check_mark: socialMedia_backend -> schemas -> comment.js

```
export default{
    name: 'comment',
    title: 'Comment',
    type: 'document',
    fields: [
        {
            name: 'postedBy',
            title: 'PostedBy',
            type: 'postedBy'
        },
        {
            name: 'comment',
            title: 'Comment',
            type: 'string'
        },
    ]
}
```
:heavy_check_mark: socialMedia_backend -> schemas -> save.js

```

export default{
    name: 'save',
    title: 'Save',
    type: 'document',
    fields: [
        {
            name: 'postedBy',
            title: 'PostedBy',
            type: 'postedBy'
        },
        {
            name: 'userId',
            title: 'UserId',
            type: 'string'
        },
    ]
}
```
:heavy_check_mark: socialMedia_backend -> schemas -> postedBy.js

```
export default{
    name: 'postedBy',
    title: 'PostedBy',
    type: 'reference',
    to: [{ type: 'user'}]
}
```
:heavy_check_mark: socialMedia_backend -> schemas -> schemas.js

```
// First, we must import the schema creator
import createSchema from 'part:@sanity/base/schema-creator'

// Then import schema types from any plugins that might expose them
import schemaTypes from 'all:part:@sanity/base/schema-type'
import user from './user';
import pin from './pin';
import comment from './comment';
import postedBy from './postedBy';
import save from './save';



// Then we give our schema to the builder and provide the result to Sanity
export default createSchema({
  // We name our schema
  name: 'default',
  // Then proceed to concatenate our document type
  // to the ones provided by any plugins that are installed
  types: schemaTypes.concat([ 
    user, pin, comment, postedBy, save
  ]),
});

```

:sparkles: Funcionou!!!

🎉 :tada: BACKEND CONCLUÍDO!

- [ ] **3) Programação Frontend** 

:heavy_check_mark: Comandos no terminal:

:heavy_check_mark: mudar diretório: cd .\socialmedia_frontend\

[Link to Install Tailwind CSS](https://tailwindcss.com/docs/guides/create-react-app) 

OBS.: Tive que colocar nome da pasta tudo em minusculo para não ter erro


:heavy_check_mark: npx create-react-app ./

:heavy_check_mark: npm install -D tailwindcss postcss autoprefixer

:heavy_check_mark: npx tailwindcss init -p



