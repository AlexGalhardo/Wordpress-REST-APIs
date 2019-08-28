### Referencias
   - https://wordpress.org/plugins/jwt-authentication-for-wp-rest-api/
      - Endpoint | HTTP Verb
         - http://localhost/wordpress/wp-json/jwt-auth/v1/token | POST
            - para autenticar usuário usando JWT no wordpress
            - ```json
			   {
				 "username": "alex@gmail.com",
				 "password": "123"
				}
			   ```
			 - será dado o token do JWT para ser usado durante as requisições deste usuário
			 - usar no JWT TOKEN: Bearer token_usuário
         - /wp-json/jwt-auth/v1/token/validate | POST     => para validar com JWT TOKEN
         - define('JWT_AUTH_SECRET_KEY', 'your-top-secret-key');
         - https://api.wordpress.org/secret-key/1.1/salt/
         - define('JWT_AUTH_CORS_ENABLE', true);
         - .htaccess
            - ```
               # BEGIN WordPress
				<IfModule mod_rewrite.c>
				RewriteEngine On
				RewriteCond %{HTTP:Authorization} ^(.*)
				RewriteRule ^(.*) - [E=HTTP_AUTHORIZATION:%1]
				RewriteBase /wordpress/
				RewriteRule ^index\.php$ - [L]
				RewriteCond %{REQUEST_FILENAME} !-f
				RewriteCond %{REQUEST_FILENAME} !-d
				RewriteRule . /wordpress/index.php [L]
				</IfModule>
				# END WordPress
              ```
         - Token JAUM = eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL3dvcmRwcmVzcyIsImlhdCI6MTU2NzAxODMzMywibmJmIjoxNTY3MDE4MzMzLCJleHAiOjE1NjcxMDQ3MzMsImRhdGEiOnsidXNlciI6eyJpZCI6IjMifX19.7hOdK7n1Qck466bXBK4KGdS9RozHvql5bqvbEgWZZP0
            - password: 666
            - username: jaum@gmail.com
         - http://localhost/wordpress/wp-json/api/produto
            - ```json
              {
			   "nome": "iphone",
			   "descricao": "produto usado",
			   "preco": "999"
			  }
              ```
          - produto_get.php
             - http://localhost/wordpress/wp-json/api/produto/alex
             - no caso, 'alex' é o nome do produto
          - http://localhost/wordpress/wp-login.php?action=lostpassword

### POST: http://localhost/wordpress/wp-json/api/usuario
   - Exemplo para adicionar novo usuário no wordpress
```json
{
 "email": "alex@gmail.com",
 "nome": "alex",
 "senha": 123,
 "rua": "Aqui Perto",
 "cep": "233322",
 "numero": "321",
 "bairro": "Ali Perto",
 "cidade": "São Carlos",
 "estado": "SP"
}
```