# RotaFácil — MVP inicial

## O que funciona nesta versão
- Cadastro de entregadores.
- Cadastro manual de pedidos.
- Importação de CSV e Excel (.xlsx/.xls).
- Exportação de pedidos em CSV.
- Captura de foto pela câmera do celular e OCR (Tesseract.js; requer internet para carregar bibliotecas/idioma).
- Geocodificação de endereços com OpenStreetMap Nominatim.
- Distribuição inicial de pedidos por proximidade e capacidade entre entregadores.
- Sequenciamento aproximado por vizinho mais próximo.
- Abertura da sequência no Google Maps.
- Mapa de pedidos geocodificados e pontos GPS.
- Compartilhamento de localização enquanto a página permanece aberta.
- Comprovante local com foto, nome/assinatura digitada e observação.
- Dados salvos no navegador via localStorage.

## Limitações importantes
Esta é uma prova de conceito/MVP local, não uma implantação multiusuário pronta para operação real:
- Os dados ficam no navegador/dispositivo. Não há sincronização entre gestor e entregadores.
- GPS em segundo plano não é garantido; iOS/Android podem suspender a página.
- Não há login, controle de acesso, API própria, notificações push nem backup central.
- O algoritmo de distribuição é heurístico (proximidade/capacidade), não um solver profissional de VRP com janelas de horário, trânsito ou restrições avançadas.
- OCR não interpreta de forma confiável todos os campos da etiqueta; o texto precisa ser revisado.
- Serviços externos de mapas/geocodificação têm limites e termos próprios. Para produção, contratar/configurar provedor e backend.

## Como testar
1. Descompacte o ZIP em um computador.
2. Execute um servidor local na pasta, por exemplo: `python -m http.server 8000`
3. Abra `http://localhost:8000` no navegador.
4. Para câmera/GPS, use HTTPS ou localhost e conceda permissões.
5. Cadastre entregadores, importe uma planilha e gere rotas.

Para instalar no celular: hospede os arquivos em um domínio HTTPS e use "Adicionar à Tela de Início" no Android/iPhone.

## Formato CSV sugerido
`pedido,destinatario,telefone,endereco,numero,bairro,cidade,uf,cep,observacao`

Antes de uso comercial, implementar backend autenticado (por exemplo Supabase), banco compartilhado, criptografia/regras de acesso, consentimento e retenção de localização, trilha de auditoria, tratamento LGPD, testes em campo e provedor de roteirização dedicado.
