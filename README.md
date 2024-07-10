# BancodeDados
Banco de dados
package ContatoDAO;

import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class Contato {

	private Connection connection;

    public Contato(Connection connection) {
        this.connection = connection;
    }

    public void adicionarContato(Contato contato) throws SQLException {
        String sql = "INSERT INTO Contato (tipo_contato, contato, pessoa_id) VALUES (?, ?, ?)";
        try (PreparedStatement stmt = connection.prepareStatement(sql)) {
            stmt.setInt(1, contato.getTipoContato());
            stmt.setLong(2, contato.getTipoContato());
            stmt.setInt(3, contato.getPessoaId());
            stmt.executeUpdate();
        }
    }

    private int getPessoaId() {
		// TODO Auto-generated method stub
		return 0;
	}

	private int getTipoContato() {
		// TODO Auto-generated method stub
		return 0;
	}

	public Contato obterContatoPorId(int id) throws SQLException {
        String sql = "SELECT * FROM Contato WHERE id = ?";
        try (PreparedStatement stmt = connection.prepareStatement(sql)) {
            stmt.setInt(1, id);
            try (ResultSet rs = stmt.executeQuery()) {
                if (rs.next()) {
                    Contato contato = new Contato(connection);
                    contato.setId(rs.getInt("id"));
                    contato.setTipoContato(rs.getInt("tipo_contato"));
                    contato.setContato(rs.getString("contato"));
                    contato.setPessoaId(rs.getInt("pessoa_id"));
                    return contato;
                }
            }
        }
        return null;
    }

    public List<Contato> listarContatosPorPessoa(int pessoaId) throws SQLException {
        List<Contato> contatos = new ArrayList<>();
        String sql = "SELECT * FROM Contato WHERE pessoa_id = ?";
        try (PreparedStatement stmt = connection.prepareStatement(sql)) {
            stmt.setInt(1, pessoaId);
            try (ResultSet rs = stmt.executeQuery()) {
                while (rs.next()) {
                    Contato contato = new Contato(connection);
                    contato.setId(rs.getInt("id"));
                    contato.setTipoContato(rs.getInt("tipo_contato"));
                    contato.setContato(rs.getString("contato"));
                    contato.setPessoaId(rs.getInt("pessoa_id"));
                    contatos.add(contato);
                }
            }
        }
        return contatos;
    }

    private void setPessoaId(int int1) {
		// TODO Auto-generated method stub
		
	}

	private void setId(int int1) {
		// TODO Auto-generated method stub
		
	}

	private void setTipoContato(int int1) {
		// TODO Auto-generated method stub
		
	}

	private void setContato(String string) {
		// TODO Auto-generated method stub
		
	}

	public void atualizarContato(Contato contato) throws SQLException {
        String sql = "UPDATE Contato SET tipo_contato = ?, contato = ?, pessoa_id = ? WHERE id = ?";
        try (PreparedStatement stmt = connection.prepareStatement(sql)) {
            stmt.setInt(1, contato.getTipoContato());
            stmt.setLong(2, contato.getTipoContato());
            stmt.setInt(3, contato.getPessoaId());
            stmt.setInt(4, contato.getId());
            stmt.executeUpdate();
        }
    }

    private int getId() {
		// TODO Auto-generated method stub
		return 0;
	}

	public void deletarContatoPorId(int id) throws SQLException {
        String sql = "DELETE FROM Contato WHERE id = ?";
        try (PreparedStatement stmt = connection.prepareStatement(sql)) {
            stmt.setInt(1, id);
            stmt.executeUpdate();
        }
    }
}

package ContatoDAO;

import java.sql.Connection;
import java.util.List;

public class ContatoDAO {

	public ContatoDAO(Connection connection) {
		// TODO Auto-generated constructor stub
	}

	public void adicionarContato(ContatoDAO contato) {
		// TODO Auto-generated method stub
		
	}

	public Contato obterContatoPorId(int id) {
		// TODO Auto-generated method stub
		return null;
	}

	public void atualizarContato(ContatoDAO contato) {
		// TODO Auto-generated method stub
		
	}

	public List<Contato> listarContatosPorPessoa(int pessoaId) {
		// TODO Auto-generated method stub
		return null;
	}

}
package ContatoJava;

public class Contatojava {
    private int id;
    private int tipoContato; // 0 para Telefone, 1 para Celular
    private String contato;
    private int pessoaId;
	public int getPessoaId() {
		return pessoaId;
	}
	public void setPessoaId(int pessoaId) {
		this.pessoaId = pessoaId;
	}
	public String getContato() {
		return contato;
	}
	public void setContato(String contato) {
		this.contato = contato;
	}
	public int getTipoContato() {
		return tipoContato;
	}
	public void setTipoContato(int tipoContato) {
		this.tipoContato = tipoContato;
	}
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}

    // Getters e Setters
}
package PessoaDAO;



	public class Pessoa {

	

	public void setId(String string) {
		// TODO Auto-generated method stub
		
	}

	public void setNome(String string) {
		// TODO Auto-generated method stub
		
	}

	public void setEndereco(String string) {
		// TODO Auto-generated method stub
		
	}

	public void setCidade(String string) {
		// TODO Auto-generated method stub
		
	}

	public void setId(int int1) {
		// TODO Auto-generated method stub
		
	}

	public String getNome() {
		// TODO Auto-generated method stub
		return null;
	}

	public String getEndereco() {
		// TODO Auto-generated method stub
		return null;
	}

	public String getCidade() {
		// TODO Auto-generated method stub
		return null;
	}

	public String getUf() {
		// TODO Auto-generated method stub
		return (String) null;
	}

	public String getCpf() {
		// TODO Auto-generated method stub
		return null;
	}

	public short getIdade() {
		// TODO Auto-generated method stub
		return 0;
	}

	public String getClasse() {
		// TODO Auto-generated method stub
		return null;
	}

}

 package PessoaDAO;

import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class PessoaDAO {

    private Connection connection;

    public PessoaDAO(Connection connection) {
        this.connection = connection;
    }

    public void criarPessoa(Pessoa pessoa) throws SQLException {
        String sql = "INSERT INTO Pessoa (nome, endereco, cep, cidade, uf) VALUES (?, ?, ?, ?, ?)";
        try (PreparedStatement stmt = connection.prepareStatement(sql)) {
        	
        	stmt.setString(1, pessoa.getNome());      // Define o primeiro parâmetro como String
        	stmt.setString(2, pessoa.getEndereco());  // Define o segundo parâmetro como String
        	stmt.setString(3, pessoa.getClasse());    // Define o terceiro parâmetro como String 
        	stmt.setString(4, pessoa.getCidade());    // Define o quarto parâmetro como String
        	stmt.setString(5, pessoa.getUf());          // Define o quinto parâmetro como Long (ou setInt() se for um int)
        	stmt.executeUpdate();                     // Executa o comando SQL

        }
    }

    public Pessoa obterPessoaPorId(int id) throws SQLException {
        String sql = "SELECT * FROM Pessoa WHERE id = ?";
        try (PreparedStatement stmt = connection.prepareStatement(sql)) {
            stmt.setInt(1, id);
            try (ResultSet rs = stmt.executeQuery()) {
                if (rs.next()) {
                    Pessoa pessoa = new Pessoa();
                    pessoa.setId(rs.getInt("id"));
                    pessoa.setNome(rs.getString("nome"));
                    pessoa.setEndereco(rs.getString("endereco"));
                    pessoa.setId(rs.getString("cep"));
                    pessoa.setCidade(rs.getString("cidade"));
                    pessoa.setId(rs.getString("uf"));
                    return pessoa;
                }
            }
        }
        return null;
    }

    public List<Pessoa> listarTodasPessoas() throws SQLException {
        List<Pessoa> pessoas = new ArrayList<>();
        String sql = "SELECT * FROM Pessoa";
        try (Statement stmt = connection.createStatement();
             ResultSet rs = stmt.executeQuery(sql)) {
            while (rs.next()) {
                Pessoa pessoa = new Pessoa();
                pessoa.setId(rs.getInt("id"));
                pessoa.setNome(rs.getString("nome"));
                pessoa.setEndereco(rs.getString("endereco"));
                pessoa.setId(rs.getString("cep"));
                pessoa.setCidade(rs.getString("cidade"));
                pessoa.setId(rs.getString("uf"));
                pessoas.add(pessoa);
            }
        }
        return pessoas;
    }

    public void atualizarPessoa(Pessoa pessoa) throws SQLException {
        String sql = "UPDATE Pessoa SET nome = ?, endereco = ?, cep = ?, cidade = ?, uf = ? WHERE id = ?";
        try (PreparedStatement stmt = connection.prepareStatement(sql)) {
        	stmt.setString(1, pessoa.getNome());
        	stmt.setString(2, pessoa.getEndereco());
        	stmt.setString(3, pessoa.getCpf()); 
        	stmt.setString(4, pessoa.getCidade());
        	stmt.setString(5, pessoa.getUf()); 
        	stmt.setShort(6, pessoa.getIdade());  
        	stmt.executeUpdate();
        }
    }

    public void deletarPessoaPorId(int id) throws SQLException {
        String sql = "DELETE FROM Pessoa WHERE id = ?";
        try (PreparedStatement stmt = connection.prepareStatement(sql)) {
            stmt.setInt(1, id);
            stmt.executeUpdate();
        }
    }
}
package PessoaJava;

public class PessoaJava {
    private int id;
    private String nome;
    private String endereco;
    private String cep;
    private String cidade;
    private String uf;
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}
	public String getEndereco() {
		return endereco;
	}
	public void setEndereco(String endereco) {
		this.endereco = endereco;
	}
	public String getCep() {
		return cep;
	}
	public void setCep(String cep) {
		this.cep = cep;
	}
	public String getCidade() {
		return cidade;
	}
	public void setCidade(String cidade) {
		this.cidade = cidade;
	}
	public String getUf() {
		return uf;
	}
	public void setUf(String uf) {
		this.uf = uf;
	}

    // Getters e Setters

}

package PessoaService;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.List;

import ContatoDAO.Contato;
import ContatoDAO.ContatoDAO;

public class PessoaService {

	private ContatoDAO contatoDAO;

    public void ContatoService() throws SQLException {
        Connection connection = DriverManager.getConnection("jdbc:h2:./test", "mi", "123");
        this.contatoDAO = new ContatoDAO(connection);
    }

    public void adicionarContato(ContatoDAO contato) throws SQLException {
        contatoDAO.adicionarContato(contato);
    }

    public Contato obterContatoPorId(int id) throws SQLException {
        return contatoDAO.obterContatoPorId(id);
    }

    public List<Contato> listarContatosPorPessoa(int pessoaId) throws SQLException {
       

 return contatoDAO.listarContatosPorPessoa(pessoaId);
    }

    public void atualizarContato(ContatoDAO contato) throws SQLException {
        contatoDAO.atualizarContato(contato);
    }

    public void deletarContatoPorId(int id) throws SQLException {
        contatoDAO.obterContatoPorId(id);
    }
}

package View;

import java.util.List;

import dm20241m.model.bean.Endereco;

public class ControllerEndereco {

	public Endereco inserir(Endereco enderecoEnt) {
		// TODO Auto-generated method stub
		return null;
	}

	public Endereco alterar(Endereco enderecoEnt) {
		// TODO Auto-generated method stub
		return null;
	}

	public Endereco buscar(Endereco enderecoEnt) {
		// TODO Auto-generated method stub
		return null;
	}

	public Endereco excluir(Endereco enderecoEnt) {
		// TODO Auto-generated method stub
		return null;
	}

	public List<Endereco> listar(Endereco enderecoEnt) {
		// TODO Auto-generated method stub
		return null;
	}

}
package View;

import dm20241m.controller.Controller;
import dm20241m.model.bean.Endereco;
import java.sql.SQLException;
import java.util.List;
import javax.swing.JOptionPane;

@SuppressWarnings("unused")
public class View {

    public static void menu() throws SQLException, ClassNotFoundException {
        String msg = " 1 - Inserir \n 2 - Alterar \n 3 - Buscar \n 4 - Excluir \n 5 - Listar ";
        int num = Integer.parseInt(JOptionPane.showInputDialog(msg));
        switch (num) {
            case 1:
                inserir();
                break;
            case 2:
                alterar();
                break;
            case 3:
                buscar();
                break;
            case 4:
                excluir();
                break;
            case 5:
                listar();
                break;
            default:
                System.out.println("Opcao inválida");
        }
    }

    private static void inserir() throws SQLException, ClassNotFoundException {
        String nome = JOptionPane.showInputDialog("NOME");
        String endereco = JOptionPane.showInputDialog("ENDEREÇO");
        String cep = JOptionPane.showInputDialog("CEP");
        String cidade = JOptionPane.showInputDialog("CIDADE");
        String uf = JOptionPane.showInputDialog("UF");
        Endereco enderecoEnt = new Endereco(0, nome, endereco, cep, cidade, uf);
        ControllerEndereco contEnd = new ControllerEndereco();
        Endereco enderecoSaida = contEnd.inserir(enderecoEnt);
        JOptionPane.showMessageDialog(null, enderecoSaida.toString());
    }

    private static void alterar() throws SQLException, ClassNotFoundException {
        int id = Integer.parseInt(JOptionPane.showInputDialog("ID"));
        String nome = JOptionPane.showInputDialog("NOME");
        String endereco = JOptionPane.showInputDialog("ENDEREÇO");
        String cep = JOptionPane.showInputDialog("CEP");
        String cidade = JOptionPane.showInputDialog("CIDADE");
        String uf = JOptionPane.showInputDialog("UF");
        Endereco enderecoEnt = new Endereco(id, nome, endereco, cep, cidade, uf);
        ControllerEndereco contEnd = new ControllerEndereco();
        Endereco enderecoSaida = contEnd.alterar(enderecoEnt);
        JOptionPane.showMessageDialog(null, enderecoSaida.toString());
    }

    private static void buscar() throws SQLException, ClassNotFoundException {
        int id = Integer.parseInt(JOptionPane.showInputDialog("ID"));
        Endereco enderecoEnt = new Endereco(id, null, null, null, null, null);
        ControllerEndereco contEnd = new ControllerEndereco();
        Endereco enderecoSaida = contEnd.buscar(enderecoEnt);
        JOptionPane.showMessageDialog(null, enderecoSaida.toString());
    }

    private static void excluir() throws SQLException, ClassNotFoundException {
        int id = Integer.parseInt(JOptionPane.showInputDialog("ID"));
        Endereco enderecoEnt = new Endereco(id, null, null, null, null, null);
        ControllerEndereco contEnd = new ControllerEndereco();
        Endereco enderecoSaida = contEnd.excluir(enderecoEnt);
        JOptionPane.showMessageDialog(null, enderecoSaida.toString());
    }

    private static void listar() throws SQLException, ClassNotFoundException {
        String nome = JOptionPane.showInputDialog("NOME");
        Endereco enderecoEnt = new Endereco(0, nome, nome, nome, nome, nome);
        ControllerEndereco contEnd = new ControllerEndereco();
        List<Endereco> listaEndereco = contEnd.listar(enderecoEnt);
        for (Endereco enderecoSaida : listaEndereco) {
            JOptionPane.showMessageDialog(null, enderecoSaida.toString());
        }
    }
}
