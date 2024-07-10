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
