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


### Módulos
	São itens de configuração que servem para agregar diretivas, serviços, pipes ou components. 
	São utilizados:
	- para organização do código, 
	- decidir o que será exportado externamente 
	- defiinir como a injeção de dependencia vai ser configurada.
	- dividir a aplicação em partes independentes e permitir que essas partesnão sejam 
	  carregas de imediato, apenas quando requisitadas
	
   **Root Module:** Módulo principal da aplicação. Tem uma referência para os demais módulos. Unico que apresenta
	bootstrap. 
    
   **Shared Module (Compartilhado):**  modulo que será compartilhado com os demais modulos. (exports)
	
	import { NgModule } from '@angular/core';
	import { FormsModule, ReactiveFormsModule } from '@angular/forms';
	import { RouterModule } from '@angular/router';

	import { CommonModule } from '@angular/common';
	import { LoadingSpinnerComponent} from './ui/loading-spinner/loading-spinner.component';
	import { ROUTES } from '../app.routes';
	

	@NgModule({
	  declarations: [
	      LoginLayoutComponent,
	   ],
	  imports: [
	    CommonModule, FormsModule, ReactiveFormsModule, RouterModule
	  ],
	  exports: [
		LoadingSpinnerComponent,
		CommonModule,
		FormsModule,
		ReactiveFormsModule,
		RouterModule
	  ]
	})
	export class SharedModule { }
    
  **Feature Module:** Contém a implementação das funcionalidades da aplicação. Importam o modulo compartilhado.
  **CoreModule:** Utilizado para organizar os providers.
   
   **Lazy-loading (carregamento tardio)** : módulo que será carregado somente se utilizado. 
	
 	
	 ROUTER 
	 		{ path: 'plans', loadChildren: './plans/plans.module#PlansModule'}
	   
	 MODULE  
	 
	               const ROUTES: Routes = [
			  {path: '', component: PlansComponent}
			];

			@NgModule({
			  declarations: [PlansComponent, PlansComponent],
			  imports: [
			     SharedModule, RouterModule.forChild(ROUTES)
			  ],
			})
			export class PlansModule { }
	
  **Pre carregamento:**: Realiza o carregamento dos modulos lazy em  backgroung.
   		
		import { RouterModule, PreloadAllModules } from '@angular/router';
		
		RouterModule.forRoot(ROUTES,{preloadingStrategy: PreloadAllModules})

