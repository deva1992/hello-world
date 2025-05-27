import java.io.OutputStream;
import java.net.HttpURLConnection;
import java.net.URL;
 
public class DlpHttpTest {
    public static void main(String[] args) throws Exception {
        String sensitiveData = "SSN: 123-45-6789";
 
        URL url = new URL("http://example.com/upload");
        HttpURLConnection conn = (HttpURLConnection) url.openConnection();
        conn.setRequestMethod("POST");
        conn.setDoOutput(true);
        conn.setRequestProperty("Content-Type", "application/x-www-form-urlencoded");
 
        try (OutputStream os = conn.getOutputStream()) {
            os.write(("data=" + sensitiveData).getBytes());
        }
 
        System.out.println("Response code: " + conn.getResponseCode());
    }
}
