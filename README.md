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

- [ ] **2) Programação** 

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
