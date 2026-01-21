# Descripción
Bot que ejecuta la estrategia de doble tap en el exchange bybit. 
 * En el código puedes ver como se interactua con el API de Bybit vía HTTP y WebSockets sin necesidad de librerías adiconales,
   también puedes ver el flujo para generar el token de seguridad y como se forman los encabezados para las peticiones web y la
   conexión inicial al WebSocket privado.
 * Puedes enviar ordenes a mercado, límite, condicionales, take profit,  stop loss.
 * Si deseas obtener información diferente a la ofrecida en el bot por ejemplo el saldo de la billetera, solo consulta en la 
   documentación de Bybit el endpoint para obtener esta información y agrega el método en la clase HTTPClient.

# Requisitos
Python 3.10+

# Instalación
En la carpeta de descarga ejecuta este comando
* pip install -r requirements.txt

# Configuración
* API_KEY = ""  Aquí estableces el API_KEY de tu cuenta.
* API_SECRET = "" Aquí estableces el API_SECRET de tu cuenta.
* Si no sabes como generar estas inforación lee el siguiente enlace https://www.bybit.com/es-MX/help-center/article/How-to-create-your-API-key
* En el método main():
  * ticker = Ticker('BCHUSDT') -Mondea o Ticker con el que se va a trabajar.
  *  await  ticker.start(
                            wallet_amount=100, #Saldo de la billetera
                            wallet_percent_first_buy=0.01,  #100% = 1, 10% = 0.1, 1% = 0.01
                            leverage=10, #Apalancamiento
                            expected_pnl=2,# USDT de ganancia para la estrategia 
                            max_risk_allowed=0.5 # 100% = 1, 50% = 0.5%
                            )    
     * wallet_amount=100 -Saldo de la billetera.
     * wallet_percent_first_buy=0.01 -Que porcentaje de la billetera se usará para la primer compra en este caso es el 1%.
     * leverage=10 -Que apalancamiento deseas utilizar en la estrategia.
     * max_risk_allowed=0.5 -Que cantidad de la billetera deseas que quede "congelado" si es que se toma una cobertura en este caso es el 50%
     * expected_pnl = 2 -Ganancia esperada en USDT la idea es que cuando se llegue a esta meta, se termine la ejecución del bot (No se encuentra implementada esta funcionalidad).
 
# Disclaimer
  * Este proyecto es de software abierto (open source) y se proporciona únicamente con fines educativos y experimentales. Es una  herramienta de apoyo para el análisis y ejecución automatizada de operaciones en mercados de criptomonedas. No constituye asesoramiento financiero ni de inversión.
  * El trading de criptomonedas implica alto riesgo y puede resultar en la pérdida parcial o total del capital invertido. Los resultados pasados, simulaciones, backtests o ejemplos mostrados no garantizan resultados futuros.
  * El usuario reconoce y acepta que:
    * Opera bajo su propio riesgo y responsabilidad.
    * Es responsable de configurar, supervisar y validar el funcionamiento del bot antes y durante su uso.
    * El desarrollador no se hace responsable por pérdidas financieras, fallos técnicos, errores de configuración, interrupciones de servicios externos (exchanges, APIs, conectividad), cambios en las condiciones del mercado o uso indebido del software.
  * Este software se proporciona “tal cual” (AS IS), sin garantías explícitas ni implícitas de ningún tipo, incluyendo —pero no limitándose a— garantías de rentabilidad, adecuación para un propósito particular o funcionamiento ininterrumpido.
  * Al utilizar este software, el usuario acepta plenamente los términos de este aviso legal.
      
  

