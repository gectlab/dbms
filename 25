CREATE TABLE Student2 (
    registernumber NUMBER PRIMARY KEY,
    name           VARCHAR2(50),
    subj1          NUMBER(5,2),
    subj2          NUMBER(5,2),
    subj3          NUMBER(5,2)
);

BEGIN
INSERT INTO Student2 VALUES (2001, 'Arjun', 85, 90, 88);
INSERT INTO Student2 VALUES (2002, 'Meera', 78, 82, 80);
INSERT INTO Student2 VALUES (2003, 'Kiran', 92, 89, 95);

COMMIT;
END;
/

CREATE OR REPLACE PACKAGE student_marks_pkg AS
    PROCEDURE get_total_marks(p_regno NUMBER);
END student_marks_pkg;
/

CREATE OR REPLACE PACKAGE BODY student_marks_pkg AS

    PROCEDURE get_total_marks(p_regno NUMBER) IS
        v_sub1 Student2.subj1%TYPE;
        v_sub2 Student2.subj2%TYPE;
        v_sub3 Student2.subj3%TYPE;
        v_total NUMBER;
    BEGIN
        SELECT subj1, subj2, subj3
        INTO v_sub1, v_sub2, v_sub3
        FROM Student2
        WHERE registernumber = p_regno;

        v_total := v_sub1 + v_sub2 + v_sub3;

        DBMS_OUTPUT.PUT_LINE('Total Marks of Register Number ' || p_regno || ' is: ' || v_total);

    EXCEPTION
        WHEN NO_DATA_FOUND THEN
            DBMS_OUTPUT.PUT_LINE('Student not found');
        WHEN OTHERS THEN
            DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
    END get_total_marks;

END student_marks_pkg;
/

BEGIN
    student_marks_pkg.get_total_marks(2001);
END;
/




