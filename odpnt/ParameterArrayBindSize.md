This property specifies the maximum size, in bytes or characters, of the data for each array element transmitted to or from the database. This property is used for Array Bind or PL/SQL Associative Array execution.

### Declaration

    // C#
    public int[] ArrayBindSize {get; set; }

### Property Value

An array of `int` values specifying the size.

### Remarks

Default = `null`.

This property is only used for variable size element types for an Array Bind or PL/SQL Associative Array. For fixed size element types, this property is ignored.

Each element in the `ArrayBindSize` corresponds to the bind size of an element in the `Value` property. Before execution, `ArrayBindSize` specifies the maximum size of each element to be bound in the `Value` property. After execution, it contains the size of each element returned in the `Value` property.

For binding a PL/SQL Associative Array, whose elements are of a variable-length element type, as an `InputOutput`, `Out`, or `ReturnValue` parameter, this property must be set properly. The number of elements in `ArrayBindSize` must be equal to the value specified in the `OracleParameter.Size` property.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class ArrayBindSizeSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleParameter[] prm = new OracleParameter[3];

        // Create OracleParameter objects through OracleParameterCollection
        OracleCommand cmd = con.CreateCommand();

        cmd.CommandText = "select max(empno) from emp";
        int maxno = int.Parse(cmd.ExecuteScalar().ToString());

        // Set the ArrayBindCount for Array Binding
        cmd.ArrayBindCount = 2;

        prm[0] = cmd.Parameters.Add("paramEmpno", OracleDbType.Decimal,
          new int[2] {maxno + 10, maxno + 11}, ParameterDirection.Input);
        prm[1] = cmd.Parameters.Add("paramEname", OracleDbType.Varchar2,
          new string[2] {"Client1xxx", "Client2xxx"}, ParameterDirection.Input);
        prm[2] = cmd.Parameters.Add("paramDeptNo", OracleDbType.Decimal,
          new int[2] {10, 10}, ParameterDirection.Input);

        // Set the ArrayBindSize for prm[1]
        // These sizes indicate the maximum size of the elements in Value property
        prm[1].ArrayBindSize = new int[2];
        prm[1].ArrayBindSize[0] = 7; // Set ename = "Client1"
        prm[1].ArrayBindSize[1] = 7; // Set ename = "Client2"

        cmd.CommandText =
          "insert into emp(empno, ename, deptno) values(:1, :2, :3)";

        cmd.ExecuteNonQuery();

        Console.WriteLine("Record for employee id {0} has been inserted.",
          maxno + 10);
        Console.WriteLine("Record for employee id {0} has been inserted.",
          maxno + 11);

        prm[0].Dispose();
        prm[1].Dispose();
        prm[2].Dispose();
        cmd.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[ArrayBindCount](CommandArrayBindCount.md)"

- "[Size](ParameterSize.md)" and "[Value](ParameterValue.md)" for more information on binding Associative Arrays

- "[ArrayBindStatus](ParameterArrayBindStatus.md)"
