using _28._2;
using System.Xml.Serialization;
using System.IO;

namespace Serializzazione
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod]
        public void TestMethod1()
        {
            Cliente cliente= new Cliente("Mario", "Rossi", "MRARSS80A01H501U", 30000);
            Banca b = new Banca();
            {
                b.Nome = "Banca1";
                b.Clienti = new List<Cliente>() { cliente};
                b.Prestiti = new List<Prestito>();
            };

            XmlSerializer serializer = new XmlSerializer(typeof(Banca));

            string path = @"C:\Users\10219\Desktop\Nuova cartella\sus.txt";

            using (FileStream fs = new FileStream(path, FileMode.Create))
            {
                serializer.Serialize(fs, b);
            }


        }
    }
}
