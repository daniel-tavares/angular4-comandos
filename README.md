# ANGULAR 4
     - Toda a aplicação angular 4 é orientada a componentes. Isso deixou a aplicação muito 
       mais facil para testar.
     - Ainda baseado em SPA (Single Page Aplication)

## Ambiente de desenvolvimento
    - Nodejs (com npm)
    - Angular CLI (npm install -g angular-cli)
    - Typescript (npm install-g typescript)
    
    
    
    
## Definições

#### Property binding ou Data binding:** 
    Vincular valor de um elemento do DOM com uma expressão angular: 
    
    
   - **ONY-WEY:** alteração de propriedade no componente reflete no template (unidirecional) 
        - [value]="valor"
    
   - **TWO-WEY:** alteração de propriedades no componente reflete no template e alteração de propriedades 
                  no template reflete no  componente (bidirecional) 
        - [(value)]="valor"


### Componentes
        Manipulam o DOM e exibem o conteudo html para o usuário.
    
### Services
        - Responsável por conter as lógica de negócio.
        
#### O que pode ser incluso em um service:
- **HttpClient:**
- **Observable:**
- **Injectable:**

        import { Injectable } from '@angular/core'
        import { HttpClient } from '@angular/common/http'
        import { Observable } from 'rxjs/Observable'
        import { Career } from "./model/career.model";
        import { apiRest } from "../app.api"
        import { ErrorHandler } from '../app.error-handler'

        @Injectable()
        export class CareerService {

	        constructor(private http: HttpClient) { }

	        findAllCareers(): Observable<Career[]> {
		        return this.http.get<Career[]>(apiRest.getCareers());
	        }
        }
        
        
### Controller

### Directives
	responsável por modificar elementos do DOM e seu comportamento.
	
- **autoGrow:** aumenta ou diminiu o tamanho de uma div.

### Roteamento
	Responsável pela navegaçãode páginas
	
### Templates
        Encapsula o código Html que será mostrado para o usuário. Pode ser: um formulário, 
	um input, um botão, etc.
        
### Metadata
        Permite ao angular ler e fazer o processamento das classes


### Injeção de dependencia





