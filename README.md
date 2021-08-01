# ficha-

/* Arquivo Pessoa.java */
package javaficha;
 
public class Pessoa {
    private String nome;        // >=6 E <=30
    private int idade;          // >0 E <100
    private float altura;       // >0
    private float peso;         // >0
    private char sexo;          // 'M' OU 'F'
 
    public void setNome(String nome){
        if( (nome.length() < 6) || (nome.length() > 30) )
            throw new IllegalArgumentException("Nome invalido. Minimo 6 caracteres, maximo 30 caracteres.");
        else
            this.nome = nome;
    }
    public void setIdade(int idade){
        if( (idade <= 0) || (idade >= 100))
            throw new IllegalArgumentException("Idade invalida. Minimo 1, maximo 99");
        else
            this.idade = idade;
    }
    public void setAltura(float altura){
        if( altura <= 0 )
            throw new IllegalArgumentException("Altura invalida. Altura deve ser maior do que 0");
        else
            this.altura = altura;
    }
    public void setPeso(float peso){
        if( peso <= 0 )
            throw new IllegalArgumentException("Peso invalido. Pesoa deve ser maior do que 0");
        else
            this.peso = peso;
    }
    public void setSexo(char sexo){
        if( (sexo != 'M') && (sexo != 'F') )
            throw new IllegalArgumentException("Sexo invalido. 'M' OU 'F' ");
        else
            this.sexo = sexo;
    }
 
    public String getNome(){
        return this.nome;
    }
    public int getIdade(){
        return this.idade;
    }
    public float getAltura(){
        return this.altura;
    }
    public float getPeso(){
        return this.peso;
    }
    public char getSexo(){
        return this.sexo;
    }
 
    public void imprimirDados(){
        System.out.println("Nome: " + nome);
        System.out.println("Idade: " + idade);
        System.out.println("Peso: " + peso);
        System.out.println("Altura: " + altura);
        System.out.println("Sexo: " + sexo);
    }
}
 
/* *************************************************************************************************** */
 
/* Arquivo javaFicha.java */
package javaficha;
 
import java.io.IOException;
import java.util.Scanner;
import java.util.logging.Level;
import java.util.logging.Logger;
 
public class JavaFicha {
 
    public static void main(String[] args) {
        Scanner leitura = new Scanner(System.in);
        String nome;
        int idade;
        float altura;
        float peso;
        char sexo;
 
        try{
            Pessoa pessoa = new Pessoa();
 
            System.out.print("Digite seu nome: ");
            nome = leitura.nextLine();
            pessoa.setNome(nome);
 
            System.out.print("Digite sua idade: ");
            idade = leitura.nextInt();
            pessoa.setIdade(idade);
 
            System.out.print("Digite sua altura: ");
            altura = leitura.nextFloat();
            pessoa.setAltura(altura);
 
            System.out.print("Digite seu peso: ");
            peso = leitura.nextFloat();
            pessoa.setPeso(peso);
 
            System.out.print("Digite seu sexo: ");   
            sexo = (char) System.in.read();
            pessoa.setSexo(sexo);
 
            pessoa.imprimirDados();
        } catch (IOException ex) {
            Logger.getLogger(JavaFicha.class.getName()).log(Level.SEVERE, null, ex);
        } catch(IllegalArgumentException ex){
            System.out.println(ex.getMessage());
        }
 
    }
 
}
