CREATE TABLE Student (
    registernumber NUMBER PRIMARY KEY,
    name VARCHAR2(50),
    course VARCHAR2(50),
    SGPA NUMBER(4,2)
);

CREATE OR REPLACE PACKAGE student_pkg AS
    PROCEDURE get_sgpa(p_regno NUMBER);
END student_pkg;
/

CREATE OR REPLACE PACKAGE BODY student_pkg AS

    PROCEDURE get_sgpa(p_regno NUMBER) IS
        v_sgpa Student.SGPA%TYPE;
    BEGIN
        SELECT SGPA
        INTO v_sgpa
        FROM Student
        WHERE registernumber = p_regno;

        DBMS_OUTPUT.PUT_LINE('SGPA of Register Number ' || p_regno || ' is: ' || v_sgpa);

    EXCEPTION
        WHEN NO_DATA_FOUND THEN
            DBMS_OUTPUT.PUT_LINE('Student not found');
        WHEN OTHERS THEN
            DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
    END get_sgpa;

END student_pkg;
/

BEGIN
    student_pkg.get_sgpa(1001);
END;
/

