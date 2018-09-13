# General Python Guidelines

Unlike PEP-8, these rules do not concern style or formatting. Instead, they are simply a collection of rules of thumb.

## General
- Always prefix helper functions/methods with `_`
- Don't call `_` functions outside of the module they are contained in. _This includes tests_.

## Testing
- Use newlines to divide tests into three distinct sections: setups, actions, and assertions.
- Don't mock or patch `_` functions in tests.
- Don't test `_` functions.
- If you are using `nosetests` or `UnitTest`, organize your tests as follows:
  - The test file should be parallel to the module. This means if you are writing tests for `services/my_awesome_code.py`, put the tests in `test/services/my_awesome_code_test.py`
  - Test cases (the classes in the test file) should be used to organize tests into sections. Usually, you will want have one test case per method/function that is being tested.
  - Tests (the functions in each class) should have descriptive names and should test a _single_ scenario.
  - Test names should be explicit and full sentences. Test names should be in the format `test_<method name>_<action>_<situation>` or `test_<method name>_<situation>_<action>`. The method name can be left out if it is a repeat of the class name.
    * Bad: `test_refund_already_refunded`
    * Good: `test_refund_raises_error_when_already_refunded`

### Examples
- Bad:
  ```
  ListTest(TestCase):

    def test_list(self):
      my_list = []

      my_list.append('a')
      self.assertIn('a', my_list)
      self.assertEqual(len(my_list), 1)

      my_list.extend(['b', 'c'])
      self.assertIn('b', my_list)
      self.assertIn('c', my_list)
      self.assertEqual(len(my_list), 3)

      my_list.remove('c')
      self.assertNotIn('c', my_list)
      self.assertEqual(len(my_list), 2)
  ```

- Good:
  ```
  AppendTest(TestCase):

    def test_appends_value_to_list(self):
      my_list = []

      my_list.append('a')

      self.assertIn('a', my_list)
      self.assertEqual(len(my_list), 1)

  ExtendTest(TestCase):

    def test_appends_elements_to_list(self):
      my_list = ['a']

      my_list.extend(['b', 'c'])

      self.assertIn('b', my_list)
      self.assertIn('c', my_list)
      self.assertEqual(len(my_list), 3)

  RemoveTest(TestCase):

    def test_removes_value_from_list(self):
      my_list = ['a', 'b', 'c']

      my_list.remove('c')

      self.assertNotIn('c', my_list)
      self.assertEqual(len(my_list), 2)
  ```

## Commenting
- Don't leave TODO comments in code. Track tasks in an appropriate task tracker instead.
