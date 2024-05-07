#import pip 
#pip.main(['install','PyPDF4'])


from PyPDF4 import PdfFileWriter, PdfFileReader 

import os

lista_arquivos = os.listdir()

for arquivo in lista_arquivos:
    if ".pdf" in arquivo:
                    
        out = PdfFileWriter() 
        file = PdfFileReader(arquivo) 
        num = file.numPages 
        
        for idx in range(num): 
        
        
                page = file.getPage(idx) 
          
        
                out.addPage(page) 
          
                password = arquivo[0:5]
                out.encrypt(password)
                arquivo_out = arquivo.replace(password, "")
                #arquivo_out = "saida\" + arquivo_out
                pasta = "saida"
        with open(pasta + "/" + arquivo_out, "wb") as f: 
          
            out.write(f)
        
